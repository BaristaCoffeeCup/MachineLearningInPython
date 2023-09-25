## 业务处理入口
func Handle(updateRequest *model.UpdateRequest) *model.DialogResponse 

### 从请求体内抽取出inputAction, dialogState, metadata三个部分
func prepareInputs(updateRequest *model.UpdateRequest) (inputAction *model.InputAction, dialogState *model.DialogState, metadata *map[string]string)