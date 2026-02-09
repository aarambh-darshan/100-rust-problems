# Solution: Serialize/Deserialize Binary Tree
```rust
struct Codec;
impl Codec {
    fn new() -> Self { Codec }
    fn serialize(&self, root: Option<Rc<RefCell<TreeNode>>>) -> String {
        fn ser(node: &Option<Rc<RefCell<TreeNode>>>, s: &mut String) {
            match node {
                None => s.push_str("null,"),
                Some(n) => { s.push_str(&format!("{},", n.borrow().val)); ser(&n.borrow().left, s); ser(&n.borrow().right, s); }
            }
        }
        let mut result = String::new(); ser(&root, &mut result); result
    }
    fn deserialize(&self, data: String) -> Option<Rc<RefCell<TreeNode>>> {
        fn de(iter: &mut std::vec::IntoIter<&str>) -> Option<Rc<RefCell<TreeNode>>> {
            match iter.next()? {
                "null" => None,
                val => Some(Rc::new(RefCell::new(TreeNode { val: val.parse().unwrap(), left: de(iter), right: de(iter) })))
            }
        }
        de(&mut data.trim_end_matches(',').split(',').collect::<Vec<_>>().into_iter())
    }
}
```
**Time**: O(n), **Space**: O(n)
