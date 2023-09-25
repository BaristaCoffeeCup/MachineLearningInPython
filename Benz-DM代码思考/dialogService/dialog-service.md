## dialog_handler.go
1. 整体服务入口：HandleDialog
    - response, err := dh.service.HandleDialog(ctx, userRequest) DM逻辑处理入口

## dialog_service.go
1. 处理逻辑入口：HandleDialog
``` golang
// 定义Service接口
type Service interface {
	HandleDialog(ctx context.Context, request *model.UserRequest) (*model.DialogResponse, error)
}

// 接口实现类
type serviceImpl struct {
	domainValidator validator.DomainValidator // 校验逻辑单元
	dialogProcessor core.DialogProcessor	// DM执行单元 
	responseBuilder responserealizer.ResponseBuilder	// 结果构造单元
}

// 结构体通过实现接口定义的方法，形成implement关系
func (service *serviceImpl) HandleDialog(ctx context.Context, request *model.UserRequest) (*model.DialogResponse, error){
    ..
}

```


## domain_vaildator.go
1. 核心组件是domainValidatorImpl，包含三个部分
### GenericDomainValidator
``` golang
func (genericDomainValidatorImpl) Validate(domain string, intent string) bool {
	return strings.EqualFold(domain, coreResourceManager.GenericDomain) &&
		!strings.EqualFold(intent, intentGenericInfo)
}

// 判断本次请求的领域等于generic 且 意图不等于generic:info

```

### ResourcesValidator
``` golang
// 核心结构体
type resourcesValidatorImpl struct {
	resourceCollections resourcecollections.CollectionsType
}

// 其中CollectionsType较为复杂
```
``` golang
// CollectionsType is a map type of ResourceType to ResourceCollection
type CollectionsType = map[ResourceType]ResourceCollection

var (
	// ResourceCollections is the default map of ResourceType to ResourceCollection
	ResourceCollections = CollectionsType{
		ResourceActionDescriptions:   GetActionDescriptions(),
		ResourceDecisionTables:       GetDecisionTables(),
		ResourceOntologies:           GetOntologies(),
		ResourceResponseRealizations: GetResponseRealizations(),
		ResourceMetaData:             GetMetaDataCollection(),
	}
)

// ResourcesValidator 对以下五种资源的校验，判断是否齐全
1. ActionDescriptions
2. DecisionTables
3. Ontologies
4. ResponseRealizations
5. MetaDataCollection

```


### HUVersionValidator
包含两个组件
1. huVersionMatcher： huVersionFromSDP 和 huVersionFromHU 版本校验
2. ResourceExtractor： 根据领域等参数从资源集合中获取到对应的资源