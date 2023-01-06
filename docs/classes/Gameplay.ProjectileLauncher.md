[Gameplay](../modules/Gameplay.Gameplay.md) / ProjectileLauncher

# ProjectileLauncher <Badge type="tip" text="Class" />

**`Description`**

投掷物 v2

**`Precautions`**

此类遵循规则：getter/setter 方法仅做简单的 get/set，不能进行其他任何类似RPC、循环、事件派发等较复杂的操作

## Hierarchy

- [`GameObject`](Gameplay.GameObject.md)

  ↳ **`ProjectileLauncher`**

## Table of contents

| Properties |
| :-----|
| **[onProjectileDestroy](Gameplay.ProjectileLauncher.md#onprojectiledestroy)**: [`MulticastDelegate`](Type.MulticastDelegate.md)<() => `void`\> <br> 投掷物被销毁时触发绑定函数|
| **[onProjectileHit](Gameplay.ProjectileLauncher.md#onprojectilehit)**: [`MulticastDelegate`](Type.MulticastDelegate.md)<(`hitActor`: `GameObject`, `normalImpulse`: [`Vector`](Type.Vector.md), `hitResult`: [`HitResult`](Gameplay.HitResult.md)) => `void`\> <br> 投掷物击中物体时触发绑定函数|
| **[onProjectileSpawned](Gameplay.ProjectileLauncher.md#onprojectilespawned)**: [`MulticastDelegate`](Type.MulticastDelegate.md)<(`spawnedInstance`: `GameObject`) => `void`\> <br> 投掷物生成实例时触发绑定函数，此回调触发时实例还没有开始移动，建议将此函数作为临时附着网格体或特效时使用|

| Accessors |
| :-----|
| **[acceleration](Gameplay.ProjectileLauncher.md#acceleration)**(): `number` <br> 加速度值，正值加速，负值减速|
| **[accelerationEnable](Gameplay.ProjectileLauncher.md#accelerationenable)**(): `boolean` <br> 投掷物是否在发射后受加速度影响|
| **[accelerationEnableDistance](Gameplay.ProjectileLauncher.md#accelerationenabledistance)**(): `number` <br> 发射后多长距离后启用加速度|
| **[accelerationEnableMode](Gameplay.ProjectileLauncher.md#accelerationenablemode)**(): [`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md) <br> 加速度按照 时间 / 距离 后生效|
| **[accelerationEnableTime](Gameplay.ProjectileLauncher.md#accelerationenabletime)**(): `number` <br> 发射后多长时间后启用加速度|
| **[collisionLossCoefficient](Gameplay.ProjectileLauncher.md#collisionlosscoefficient)**(): `number` <br> 投掷物每次执行穿透后速度衰减的系数，系数为正，每次穿透后速度减少，系数为负，每次穿透后速度增加。|
| **[collisionMode](Gameplay.ProjectileLauncher.md#collisionmode)**(): [`ProjectileCollisionMode`](../enums/Gameplay.ProjectileCollisionMode.md) <br> 投掷物碰撞后如何运动：穿透/反弹|
| **[detectionRadius](Gameplay.ProjectileLauncher.md#detectionradius)**(): `number` <br> 投掷物检测碰撞的宽度|
| **[gravitationalAcceleration](Gameplay.ProjectileLauncher.md#gravitationalacceleration)**(): `number` <br> 重力值，正值重力向下，负值重力向上|
| **[gravityEnable](Gameplay.ProjectileLauncher.md#gravityenable)**(): `boolean` <br> 投掷物是否在发射后受重力影响|
| **[gravityEnableDistance](Gameplay.ProjectileLauncher.md#gravityenabledistance)**(): `number` <br> 发射后多长距离后启用重力|
| **[gravityEnableMode](Gameplay.ProjectileLauncher.md#gravityenablemode)**(): [`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md) <br> 重力按照 时间 / 距离 后生效|
| **[gravityEnableTime](Gameplay.ProjectileLauncher.md#gravityenabletime)**(): `number` <br> 发射后多长时间后启用重力|
| **[initialSpeed](Gameplay.ProjectileLauncher.md#initialspeed)**(): `number` <br> 投掷物发射的初始速度|
| **[isAutoDestroy](Gameplay.ProjectileLauncher.md#isautodestroy)**(): `boolean` <br> 投掷物超出有效射程距离或者运动持续时间后自动销毁|
| **[launchDirection](Gameplay.ProjectileLauncher.md#launchdirection)**(): [`Rotation`](Type.Rotation.md) <br> 投掷物发射方向|
| **[lifeSpan](Gameplay.ProjectileLauncher.md#lifespan)**(): `number` <br> 投掷物运动持续时间，超出后投掷物不再运动。|
| **[maxCollisionTimes](Gameplay.ProjectileLauncher.md#maxcollisiontimes)**(): `number` <br> 允许投掷物执行穿透的次数，超出次数后，再次碰撞投掷物不再移动。|
| **[maxSpeed](Gameplay.ProjectileLauncher.md#maxspeed)**(): `number` <br> 投掷物发射后的最大速度|
| **[range](Gameplay.ProjectileLauncher.md#range)**(): `number` <br> 投掷物有效射程距离，超出后投掷物不再运动。|
| **[startLocation](Gameplay.ProjectileLauncher.md#startlocation)**(): [`Vector`](Type.Vector.md) <br> 投掷物起始位置|
| **[traceLineStyle](Gameplay.ProjectileLauncher.md#tracelinestyle)**(): [`ProjectileLineStyle`](../enums/Gameplay.ProjectileLineStyle.md) <br> 轨迹风格|

| Methods |
| :-----|
| **[bindPlayer](Gameplay.ProjectileLauncher.md#bindplayer)**([`Player`](Gameplay.Player.md)): `boolean` <br> 绑定玩家|
| **[drawPredictedTrajectory](Gameplay.ProjectileLauncher.md#drawpredictedtrajectory)**(`number`, `number`): `void` <br> 绘制路径预测的轨迹，调一次开启，掉第二次即关闭，如此循环|
| **[predictedTrajectory](Gameplay.ProjectileLauncher.md#predictedtrajectory)**(`number`, `number`): [`Vector`](Type.Vector.md)[] <br> 获取路径预测的轨迹|
| **[spawnProjectileInstanceLaunch](Gameplay.ProjectileLauncher.md#spawnprojectileinstancelaunch)**(): [`ProjectileInst`](Gameplay.ProjectileInst.md) <br> 发射子弹实例|
| **[spawnProjectileInstanceLaunchToTarget](Gameplay.ProjectileLauncher.md#spawnprojectileinstancelaunchtotarget)**([`Vector`](Type.Vector.md), `number`, `number`): [`ProjectileInst`](Gameplay.ProjectileInst.md) <br> 发射子弹实例|
| **[unbindPlayer](Gameplay.ProjectileLauncher.md#unbindplayer)**(): `void` <br> 解绑玩家|

## Properties

### onProjectileDestroy

• **onProjectileDestroy**: [`MulticastDelegate`](Type.MulticastDelegate.md)<() => `void`\>

**`Description`**

投掷物被销毁时触发绑定函数

**`Precautions`**

所有投掷物都是使用的同一个回调，请不要循环添加事件绑定函数

___

### onProjectileHit

• **onProjectileHit**: [`MulticastDelegate`](Type.MulticastDelegate.md)<(`hitActor`: `GameObject`, `normalImpulse`: [`Vector`](Type.Vector.md), `hitResult`: [`HitResult`](Gameplay.HitResult.md)) => `void`\>

**`Description`**

投掷物击中物体时触发绑定函数

**`Precautions`**

所有投掷物都是使用的同一个回调，请不要循环添加事件绑定函数

___

### onProjectileSpawned

• **onProjectileSpawned**: [`MulticastDelegate`](Type.MulticastDelegate.md)<(`spawnedInstance`: `GameObject`) => `void`\>

**`Description`**

投掷物生成实例时触发绑定函数，此回调触发时实例还没有开始移动，建议将此函数作为临时附着网格体或特效时使用

**`Precautions`**

所有投掷物都是使用的同一个回调，请不要循环添加事件绑定函数

## Accessors

### acceleration

• `get` **acceleration**(): `number`

**`Description`**

加速度值，正值加速，负值减速

#### Returns

`number`

• `set` **acceleration**(`value`): `void`

**`Description`**

加速度值，正值加速，负值减速

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### accelerationEnable

• `get` **accelerationEnable**(): `boolean`

**`Description`**

投掷物是否在发射后受加速度影响

#### Returns

`boolean`

• `set` **accelerationEnable**(`value`): `void`

**`Description`**

投掷物是否在发射后受加速度影响

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `boolean` |

#### Returns

`void`

___

### accelerationEnableDistance

• `get` **accelerationEnableDistance**(): `number`

**`Description`**

发射后多长距离后启用加速度

#### Returns

`number`

• `set` **accelerationEnableDistance**(`value`): `void`

**`Description`**

发射后多长距离后启用加速度

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### accelerationEnableMode

• `get` **accelerationEnableMode**(): [`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md)

**`Description`**

加速度按照 时间 / 距离 后生效

#### Returns

[`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md)

• `set` **accelerationEnableMode**(`value`): `void`

**`Description`**

加速度按照 时间 / 距离 后生效

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md) |

#### Returns

`void`

___

### accelerationEnableTime

• `get` **accelerationEnableTime**(): `number`

**`Description`**

发射后多长时间后启用加速度

#### Returns

`number`

• `set` **accelerationEnableTime**(`value`): `void`

**`Description`**

发射后多长时间后启用加速度

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### collisionLossCoefficient

• `get` **collisionLossCoefficient**(): `number`

**`Description`**

投掷物每次执行穿透后速度衰减的系数，系数为正，每次穿透后速度减少，系数为负，每次穿透后速度增加。

#### Returns

`number`

• `set` **collisionLossCoefficient**(`value`): `void`

**`Description`**

投掷物每次执行穿透后速度衰减的系数，系数为正，每次穿透后速度减少，系数为负，每次穿透后速度增加。

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### collisionMode

• `get` **collisionMode**(): [`ProjectileCollisionMode`](../enums/Gameplay.ProjectileCollisionMode.md)

**`Description`**

投掷物碰撞后如何运动：穿透/反弹

#### Returns

[`ProjectileCollisionMode`](../enums/Gameplay.ProjectileCollisionMode.md)

• `set` **collisionMode**(`value`): `void`

**`Description`**

投掷物碰撞后如何运动：穿透/反弹

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`ProjectileCollisionMode`](../enums/Gameplay.ProjectileCollisionMode.md) |

#### Returns

`void`

___

### detectionRadius

• `get` **detectionRadius**(): `number`

**`Description`**

投掷物检测碰撞的宽度

#### Returns

`number`

• `set` **detectionRadius**(`value`): `void`

**`Description`**

投掷物检测碰撞的宽度

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`


### gravitationalAcceleration

• `get` **gravitationalAcceleration**(): `number`

**`Description`**

重力值，正值重力向下，负值重力向上

#### Returns

`number`

• `set` **gravitationalAcceleration**(`value`): `void`

**`Description`**

重力值，正值重力向下，负值重力向上

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### gravityEnable

• `get` **gravityEnable**(): `boolean`

**`Description`**

投掷物是否在发射后受重力影响

#### Returns

`boolean`

• `set` **gravityEnable**(`value`): `void`

**`Description`**

投掷物是否在发射后受重力影响

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `boolean` |

#### Returns

`void`

___

### gravityEnableDistance

• `get` **gravityEnableDistance**(): `number`

**`Description`**

发射后多长距离后启用重力

#### Returns

`number`

• `set` **gravityEnableDistance**(`value`): `void`

**`Description`**

发射后多长距离后启用重力

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### gravityEnableMode

• `get` **gravityEnableMode**(): [`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md)

**`Description`**

重力按照 时间 / 距离 后生效

#### Returns

[`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md)

• `set` **gravityEnableMode**(`value`): `void`

**`Description`**

重力按照 时间 / 距离 后生效

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`ProjectileAccelerationEnableMode`](../enums/Gameplay.ProjectileAccelerationEnableMode.md) |

#### Returns

`void`

___

### gravityEnableTime

• `get` **gravityEnableTime**(): `number`

**`Description`**

发射后多长时间后启用重力

#### Returns

`number`

• `set` **gravityEnableTime**(`value`): `void`

**`Description`**

发射后多长时间后启用重力

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`


### initialSpeed

• `get` **initialSpeed**(): `number`

**`Description`**

投掷物发射的初始速度

#### Returns

`number`

• `set` **initialSpeed**(`value`): `void`

**`Description`**

投掷物发射的初始速度

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### isAutoDestroy

• `get` **isAutoDestroy**(): `boolean`

**`Description`**

投掷物超出有效射程距离或者运动持续时间后自动销毁

#### Returns

`boolean`

• `set` **isAutoDestroy**(`value`): `void`

**`Description`**

投掷物超出有效射程距离或者运动持续时间后自动销毁

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `boolean` |

#### Returns

`void`

___

### launchDirection

• `get` **launchDirection**(): [`Rotation`](Type.Rotation.md)

**`Description`**

投掷物发射方向

#### Returns

[`Rotation`](Type.Rotation.md)

• `set` **launchDirection**(`value`): `void`

**`Description`**

投掷物发射方向

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`Rotation`](Type.Rotation.md) |

#### Returns

`void`

___

### lifeSpan

• `get` **lifeSpan**(): `number`

**`Description`**

投掷物运动持续时间，超出后投掷物不再运动。

#### Returns

`number`

• `set` **lifeSpan**(`value`): `void`

**`Description`**

投掷物运动持续时间，超出后投掷物不再运动。

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`


### maxCollisionTimes

• `get` **maxCollisionTimes**(): `number`

**`Description`**

允许投掷物执行穿透的次数，超出次数后，再次碰撞投掷物不再移动。

#### Returns

`number`

• `set` **maxCollisionTimes**(`value`): `void`

**`Description`**

允许投掷物执行穿透的次数，超出次数后，再次碰撞投掷物不再移动。

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`

___

### maxSpeed

• `get` **maxSpeed**(): `number`

**`Description`**

投掷物发射后的最大速度

#### Returns

`number`

• `set` **maxSpeed**(`value`): `void`

**`Description`**

投掷物发射后的最大速度

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`


### range

• `get` **range**(): `number`

**`Description`**

投掷物有效射程距离，超出后投掷物不再运动。

#### Returns

`number`

• `set` **range**(`value`): `void`

**`Description`**

投掷物有效射程距离，超出后投掷物不再运动。

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | `number` |

#### Returns

`void`


### startLocation

• `get` **startLocation**(): [`Vector`](Type.Vector.md)

**`Description`**

投掷物起始位置

#### Returns

[`Vector`](Type.Vector.md)

• `set` **startLocation**(`value`): `void`

**`Description`**

投掷物起始位置

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`Vector`](Type.Vector.md) |

#### Returns

`void`


### traceLineStyle

• `get` **traceLineStyle**(): [`ProjectileLineStyle`](../enums/Gameplay.ProjectileLineStyle.md)

**`Description`**

轨迹风格

#### Returns

[`ProjectileLineStyle`](../enums/Gameplay.ProjectileLineStyle.md)

• `set` **traceLineStyle**(`value`): `void`

**`Description`**

轨迹风格

#### Parameters

| Name | Type |
| :------ | :------ |
| `value` | [`ProjectileLineStyle`](../enums/Gameplay.ProjectileLineStyle.md) |

#### Returns

`void`


## Methods

### bindPlayer

▸ **bindPlayer**(`player`): `boolean`

**`Description`**

绑定玩家

**`Effect`**

客户端调用自动广播

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `player` | [`Player`](Gameplay.Player.md) |  玩家类 |

#### Returns

`boolean`

true：参数 player 有效，绑定成功


### drawPredictedTrajectory

▸ **drawPredictedTrajectory**(`density?`, `duration?`): `void`

**`Description`**

绘制路径预测的轨迹，调一次开启，掉第二次即关闭，如此循环

**`Precautions`**

如果只绘制了一个点，可能投掷物被卡住了

**`Effect`**

只在客户端调用生效

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `density?` | `number` |  密度，值越大路径点越密，性能消耗越大 default: 15 |
| `duration?` | `number` |  预测的时长 default: 2 |

#### Returns

`void`


### predictedTrajectory

▸ **predictedTrajectory**(`density`, `duration`): [`Vector`](Type.Vector.md)[]

**`Description`**

获取路径预测的轨迹

**`Effect`**

调用端生效

**`Precautions`**

如果返回的数组长度为1，可能投掷物被卡住了

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `density` | `number` |  密度，值越大路径点越细，性能消耗越大 |
| `duration` | `number` |  预测的时长 |

#### Returns

[`Vector`](Type.Vector.md)[]

路径轨迹点


### spawnProjectileInstanceLaunch

▸ **spawnProjectileInstanceLaunch**(): [`ProjectileInst`](Gameplay.ProjectileInst.md)

**`Description`**

发射子弹实例

**`Precautions`**

发射后再更新其他属性无法对本次发射的子弹产生影响；允许重复发射，注意服务端发射时，返回的值是无效的

**`Effect`**

调用端生效

#### Returns

[`ProjectileInst`](Gameplay.ProjectileInst.md)

投掷物v2实例

___

### spawnProjectileInstanceLaunchToTarget

▸ **spawnProjectileInstanceLaunchToTarget**(`location`, `time?`, `speed?`): [`ProjectileInst`](Gameplay.ProjectileInst.md)

**`Description`**

发射子弹实例

**`Precautions`**

发射后再更新其他属性无法对本次发射的子弹产生影响；允许重复发送

**`Effect`**

调用端生效

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `location` | [`Vector`](Type.Vector.md) |  发射位置 |
| `time?` | `number` | 最大飞行时长 default:5 |
| `speed?` | `number` | 初始速度 default:1000 |

#### Returns

[`ProjectileInst`](Gameplay.ProjectileInst.md)

投掷物v2实例

___

### unbindPlayer

▸ **unbindPlayer**(): `void`

**`Description`**

解绑玩家

**`Effect`**

客户端调用自动广播

#### Returns

`void`