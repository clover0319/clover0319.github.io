---
layout: post
title: "二叉查找树"
description: ""
category: 数据结构
tags: [树]
---
{% include JB/setup %}
# 二叉查找树的实现（java）
---


[原文地址](http://blog.csdn.net/kimylrong/article/details/21872909)
	

* **二叉查找树（二叉排序树）**<br>

	![Alt text](/image/tree-a.jpeg)<br>
	（图a）<br>
	二叉查找树是一种动态查找表（图a），具有这些性质：                                 
	（1）若它的左子树不为空，则左子树上的所有节点的值都小于它的根节点的值；<br>
	（2）若它的右子树不为空，则右子树上所有节点的值都大于它的根节点的值；<br>
	（3）其他的左右子树也分别为二叉查找树；<br>
	（4）二叉查找树是动态查找表，在查找的过程中可见添加和删除相应的元素，在这些操作中需要保持二叉查找树的以上性质。<br>
    java代码:<br>
    `

public class BinarySearchTree<T extends Comparable<T>> {
	private Node<T> root;

	public void insert(T element) {
		if (element == null) {
			throw new IllegalArgumentException("element can not be null");
		}

		if (root == null) {
			root = new Node<T>(null, element);
		} else {
			Node<T> node = root;
			while (true) {
				if (element.compareTo(node.value) <= 0) {
					if (node.left == null) {
						Node<T> newNode = new Node<T>(node, element);
						node.left = newNode;
						break;
					} else {
						node = node.left;
					}
				} else {
					if (node.right == null) {
						Node<T> newNode = new Node<T>(node, element);
						node.right = newNode;
						break;
					} else {
						node = node.right;
					}
				}
			}
		}
	}

	private int childCount(Node<T> node) {
		if (node == null) {
			throw new IllegalArgumentException("node can not be null");
		}

		int count = 0;

		if (node.left != null) {
			count++;
		}

		if (node.right != null) {
			count++;
		}

		return count;
	}

	public void delete(Node<T> node) {
		if (node == null) {
			throw new IllegalArgumentException("node can not be null");
		}

		int childCount = childCount(node);
		Node<T> parentNode = node.parent;

		if (childCount == 0) {
			if (parentNode == null) {
				// node is root
				root = null;
			} else {
				if (node == parentNode.left) {
					parentNode.left = null;
				} else {
					parentNode.right = null;
				}
			}
		} else if (childCount == 1) {
			if (parentNode == null) {
				// node is root, set child of node to be new root
				if (node.left != null) {
					root = node.left;
					node.left.parent = null;
				} else {
					root = node.right;
					node.right.parent = null;
				}
			} else {
				if (node == parentNode.left) {
					if (node.left != null) {
						parentNode.left = node.left;
						node.left.parent = parentNode;
					} else {
						parentNode.left = node.right;
						node.right.parent = parentNode;
					}
				} else {
					if (node.left != null) {
						parentNode.right = node.left;
						node.left.parent = parentNode;
					} else {
						parentNode.right = node.right;
						node.right.parent = parentNode;
					}
				}
			}
		} else {
			// successor has no left child
			Node<T> successor = min(node);

			if (successor != node.right) {
				transplant(successor, successor.right);

				successor.right = node.right;
				node.right.parent = successor;
			}

			transplant(node, successor);

			successor.left = node.left;
			node.left.parent = successor;
		}
	}

	private void transplant(Node<T> u, Node<T> v) {
		if (u == null) {
			throw new IllegalArgumentException("node can not be null");
		}

		if (u.parent == null) {
			root = v;
		} else if (u == u.parent.left) {
			u.parent.left = v;
		} else {
			u.parent.right = v;
		}

		if (v != null) {
			v.parent = u.parent;
		}
	}

	public Node<T> search(T element) {
		if (element == null) {
			throw new IllegalArgumentException("element can not be null");
		}

		Node<T> node = root;
		while (node != null) {
			if (node.value.equals(element)) {
				return node;
			} else if (element.compareTo(node.value) < 0) {
				node = node.left;
			} else {
				node = node.right;
			}
		}

		return null;
	}

	public Node<T> min(Node<T> rootNode) {
		if (rootNode == null) {
			throw new IllegalArgumentException("node can not be null");
		}

		Node<T> node = rootNode;
		while (node.left != null) {
			node = node.left;
		}

		return node;
	}

	public Node<T> min() {
		if (root != null) {
			return min(root);
		} else {
			return null;
		}
	}

	public Node<T> max(Node<T> rootNode) {
		if (rootNode == null) {
			throw new IllegalArgumentException("node can not be null");
		}

		Node<T> node = rootNode;
		while (node.right != null) {
			node = node.right;
		}

		return node;
	}

	public Node<T> max() {
		if (root != null) {
			return max(root);
		} else {
			return null;
		}
	}

	public Node<T> successor(Node<T> node) {
		if (node == null) {
			throw new IllegalArgumentException("node can not be null");
		}

		if (node.right != null) {
			return min(node.right);
		}

		Node<T> processNode = node;
		Node<T> parent = processNode.parent;
		while (parent != null && processNode == parent.right) {
			processNode = parent;
			parent = processNode.parent;
		}

		return parent;
	}

	public Node<T> predecesssor(Node<T> node) {
		if (node == null) {
			throw new IllegalArgumentException("node can not be null");
		}

		if (node.left != null) {
			return max(node.left);
		}

		Node<T> processNode = node;
		Node<T> parent = processNode.parent;
		while (parent != null && processNode == parent.left) {
			processNode = parent;
			parent = processNode.parent;
		}

		return parent;
	}

	public void print() {
		print(root);
	}

	public void print(Node<T> node) {
		if (node == null) {
			return;
		}

		print(node.left);
		System.out.print("  " + node.value.toString() + "  ");
		print(node.right);
	}

	public static class Node<T extends Comparable<T>> {
		private Node<T> parent;
		private Node<T> left;
		private Node<T> right;

		private T value;

		public Node(Node<T> parent, T value) {
			this.parent = parent;
			this.value = value;
		}

		public Node<T> getParent() {
			return parent;
		}

		public void setParent(Node<T> parent) {
			this.parent = parent;
		}

		public Node<T> getLeft() {
			return left;
		}

		public void setLeft(Node<T> left) {
			this.left = left;
		}

		public Node<T> getRight() {
			return right;
		}

		public void setRight(Node<T> right) {
			this.right = right;
		}

		public T getValue() {
			return value;
		}

		public void setValue(T value) {
			this.value = value;
		}
	}

	public static void main(String[] args) {
		BinarySearchTree<Integer> tree = new BinarySearchTree<Integer>();

		tree.insert(45);
		tree.insert(12);
		tree.insert(54);
		tree.insert(3);
		tree.insert(50);
		tree.insert(5);
		tree.insert(43);

		tree.print();
		System.out.println();

		Node<Integer> moneyNode = tree.search(5);
		tree.print(moneyNode);
		System.out.println();

		tree.insert(55);
		tree.print(moneyNode);
		System.out.println();

		tree.delete(moneyNode);
		tree.print();
		System.out.println();
	}
}

	
	`



 


