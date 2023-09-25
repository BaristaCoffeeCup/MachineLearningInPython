## 基本作用
DomainHistory使用类似于栈的结构存储每一轮历史对话的领域信息，栈与栈元素的结构如下：
``` golang

// 栈元素
type historyElement struct {
	Name          string `json:"name"`
	DialogActType string `json:"dialogActType"`
}

// 领域历史栈，使用切片实现
type DomainHistory struct {
	history []historyElement
}

```
栈顶的元素位于切片的末尾，栈中每一个元素仅能存在一次，如果一个已经存在于栈中的元素被再次压栈，则将该元素从栈中取出并放到栈顶
