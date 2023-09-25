## 核心能力
构建并更新对话状态

### DialogState 对话状态结构体
``` golang

// DialogState holds the current multi-domain state of the dialog.
type DialogState struct {
    // 对话历史领域信息
	LastDomains        utils.DomainHistory           `json:"lastDomains"`
	Domains            map[string]*DomainDialogState `json:"domains"`
	Metadata           map[string]*Slot              `json:"metadata,omitempty"`
	Context            map[string]*Slot              `json:"context,omitempty"`
	CurrentInputAction *InputAction                  `json:"-"`
}

// DomainDialogState holds the current state of the respective domain
type DomainDialogState struct {
	Domain           string            `json:"domain"`
	Intent           Slot              `json:"intent"`
	UserSlots        map[string]*Slot  `json:"userSlots"`
	Requests         []Slot            `json:"requests,omitempty"`
	APISlots         map[string]*Slot  `json:"apiSlots"`
	APIData          interface{}       `json:"apiData"`
	APIDataType      string            `json:"apiDataType"`
	LastDialogAction DeterminedActions `json:"lastDialogAction"`
}

// Slot structure defines all information relevant for processing one slot (user, api, intent, request)
type Slot struct {
	Name    string `json:"name"`
	Value   string `json:"value"`
	Updated bool   `json:"updated"`
}

// InputAction holds data for an input action.
type InputAction struct {
	Domain      string            `json:"domain"`
	Intent      string            `json:"intent"`
	UserInput   map[string]string `json:"userInput"`
	APIInput    map[string]string `json:"apiInput"`
	APIData     interface{}       `json:"apiData,omitempty"`
	APIDataType string            `json:"apiDataType,omitempty"`
}

// Interpretation represents one interpretation of the embedded NLU
// with a confidence, a set of intput actions, and the corresponging
// ASR hypothesis as Orthography.
type Interpretation struct {
	Confidence   string         `json:"confidence"`
	InputActions []*InputAction `json:"inputActions"`
	Orthography  string         `json:"orthography"`
}

```