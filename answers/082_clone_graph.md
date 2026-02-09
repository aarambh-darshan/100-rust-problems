# Solution: Clone Graph
```rust
use std::collections::HashMap;
impl Solution {
    pub fn clone_graph(node: Option<Rc<RefCell<Node>>>) -> Option<Rc<RefCell<Node>>> {
        fn dfs(node: &Rc<RefCell<Node>>, clones: &mut HashMap<i32, Rc<RefCell<Node>>>) -> Rc<RefCell<Node>> {
            if let Some(clone) = clones.get(&node.borrow().val) { return Rc::clone(clone); }
            let clone = Rc::new(RefCell::new(Node { val: node.borrow().val, neighbors: vec![] }));
            clones.insert(node.borrow().val, Rc::clone(&clone));
            for n in &node.borrow().neighbors { clone.borrow_mut().neighbors.push(dfs(n, clones)); }
            clone
        }
        node.map(|n| dfs(&n, &mut HashMap::new()))
    }
}
```
**Time**: O(V+E), **Space**: O(V)
