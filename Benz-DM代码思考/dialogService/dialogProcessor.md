## 核心组件
``` golang

type DialogProcessor interface {
	Process(ctx context.Context, request *model.UserRequest, domain string) *coreModel.DialogResponse
}

type dialogProcessorImpl struct {
	dialogCore      dialogCore
	domainManager   domainmanager.DomainManager
	gen20xAdapter   mapper.Gen20xAdapter
	maxApiCallCount int
}

```


