# Red-Black Tree Implementation

## Overview

This Java project implements a Red-Black Tree (RBT), a self-balancing binary search tree that maintains balanced height with insertions and deletions. The implementation includes all standard RBT operations along with comprehensive testing for the three main insertion cases.

## Features

- **Red-Black Tree Properties**:
  - Every node is either red or black (represented by `blackHeight` 0 or 1)
  - Root is always black
  - No two adjacent red nodes (red node cannot have red parent or red children)
  - Every path from a node to its descendant leaves contains the same number of black nodes

- **Core Operations**:
  - Insertion with automatic rebalancing
  - Deletion (without rebalancing in this implementation)
  - Search (contains)
  - Traversals (in-order and level-order)

- **Special Methods**:
  - Tree visualization with node colors
  - Comprehensive test cases for all RBT insertion scenarios

## Implementation Details

### Node Structure
Each node contains:
- Data value (generic type T)
- `blackHeight` (0=red, 1=black)
- Context array storing parent, left child, and right child references

### Key Methods
- `insert(T data)`: Inserts data while maintaining RBT properties
- `enforceRBTreePropertiesAfterInsert()`: Handles the three RBT insertion cases
- `rotate()`: Performs left or right rotations
- Various traversal methods including color-aware versions

## Testing

The implementation includes JUnit tests for all three RBT insertion cases:

1. **Case 1**: Parent's sibling is black and parent/child form a straight line
2. **Case 2**: Parent's sibling is black but parent/child form a triangle
3. **Case 3**: Parent's sibling is red (color flip case)

Each test verifies both the structure and coloring of the tree after operations.

## Usage

To use this Red-Black Tree implementation:

```java
// Create a new Red-Black Tree
RedBlackTree<Integer> rbt = new RedBlackTree<>();

// Insert values
rbt.insert(10);
rbt.insert(20);
rbt.insert(30);

// Check if tree contains a value
boolean contains = rbt.contains(20);

// Get tree as string
System.out.println(rbt.toString());

// Remove a value
rbt.remove(20);
```

## Visualization Methods

The class provides special methods to view the tree structure with node colors:

- `toLevelOrderStringWithColor()`: Shows level-order traversal with node colors
- `toInOrderStringWithColor()`: Shows in-order traversal with node colors

Example output:
```
[ 20(1), 10(1), 40(1), 30(0), 50(0) ]  // level-order with colors
[ 10(1), 20(1), 30(0), 40(1), 50(0) ]  // in-order with colors
```

## Limitations

- The current implementation does not rebalance after deletion
- No serialization/deserialization support
- Basic error handling with exceptions
