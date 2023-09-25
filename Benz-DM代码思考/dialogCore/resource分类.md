## ontology
``` json

{
	"ontology": {
		"intents": {
			"activate": {
				"slotOnly": false
			},
			"deactivate": {
				"slotOnly": false
			},
			"fold": {
				"slotOnly": false
			},
			"newIntent": {
				"slotOnly": false
			},
			"activate2": {
				"slotOnly": false
			},
			"deactivate2": {
				"slotOnly": false
			},
			"fold2": {
				"slotOnly": false
			}
		},
		"userInputs": {
			"slotFold": {
				"type": "StaticList",
				"valueType": "String",
				"values": {
					"headRestraints": [],
					"trailerCoupling": [],
					"exteriorMirrors": [],
					"": []
				},
				"volatile": false
			},
			"feature": {
				"type": "StaticList",
				"valueType": "String",
				"values": {
					"electronicStabilityProgram": [],
					"parkingAssistantParktronic": [],
					"dsr": [],
					"steeringAssist": [],
					"carWashMode": [],
					"hazardWarningLamps": [],
					"activeLaneKeepingAssist": [],
					"windshieldWipers": [],
					"windshieldWipersRear": [],
					"": []
				},
				"volatile": false
			}
		},
		"apiInputs": {
			"select-answer": {
				"volatile": false
			},
			"answer-id": {
				"volatile": false
			},
			"carModel": {
				"volatile": false
			},
			"ntgVersion": {
				"volatile": false
			},
			"market": {
				"volatile": false
			},
			"application": {
				"volatile": false
			},
			"seatIdentifier": {
				"volatile": false
			},
			"primaryFuelType": {
				"volatile": false
			},
			"secondaryFuelType": {
				"volatile": false
			}
		}
	},
	"domain": "carfunctions"
}

```

## actionDescription


## decisionTable


## responseRealization


## meta
当前领域所支持的车机版本元数据
``` json

{
	"ntgVersions": ["NTG7-SOP", "NTG7-FU2", "NTG7-FU3", "NTG7-FU4"],
	"version": "1.0.0",
	"owner": "BERND SCHNEPF",
	"domain": "ExpMeExpressions"
}

```