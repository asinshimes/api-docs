[ANIMATIONS](../groups/Core.ANIMATIONS.md) / Animation

# Animation <Badge type="tip" text="Class" /> <Score text="Animation" />

<p class="content-big"> 动画 </p>

<p class="content-big"> ------------------------- </p>

<p class="content-big"> 动画用于表现一个独立的动作。 </p>

<p class="content-big"> 如何使用 Animation ？ </p>

<p class="content-big"> · 想要播放一个动画资源, 需要执行 Character 中 loadAnimation 方法, 先进行资源下载, 再加载一个动画对象。 </p>

<p class="content-big"> · loop 、length、speed 属性表示对动画姿态对象一些修改；调用 play 方法, 播放这个动画对象。 </p>

<p class="content-big"> · 停止一个动画对象, 可以直接对动画对象调用 stop 。 </p>

<p class="content-big"> · 在播放步骤中, 你可以在调用 play 函数前给动画对象 onFinished 代理添加一个回调函数。因为动画的播放仅在客户端进行, 所以播放完成回调只会在客户端触发. 播放完成回调只会在动画自然播放完成后触发, 在动画播放途中调用stop(), 或者播放其他动画打断当前正在播放的动画均不会触发播放完成回调。 </p>

<p class="content-big"> 我应该在客户端还是服务器上加载动画 ？ </p>

<p class="content-big"> · 在调用 play 时, 会根据自动当前角色的网络状态及所处的端判断是否进行网络同步。 </p>

<p class="content-big"> · 如果角色在服务端, 则在所有客户端执行动画播放（动画首先在服务器上创建并复制到客户端）; </p>
如果角色在客户端, 则直接在本地播放动画.

::: warning Precautions

请不要直接使用new创建，loadAnimation可以返回动画, 以进行更加精细的动画控制。

:::

## Table of contents

### Constructors <Score text="Constructors" /> 
| :----- |

### Accessors <Score text="Accessors" /> 
| **[assetId](mw.Animation.md#assetid)**(): `string`  |
| :-----|
| 之后会开启开发者上传其制作的动画资源通道，将其上传到MW编辑器后，可以使用自己上传的动画资源。|
| **[isPlaying](mw.Animation.md#isplaying)**(): `boolean`  |
| 是否播放|
| **[length](mw.Animation.md#length)**(): `number`  |
| 获取动画时长。当前动画对象中关联的动画的时长以秒为单位。|
| **[loop](mw.Animation.md#loop)**(): `number`  |
| 设置动画的播放循环次数.|
| **[onFinish](mw.Animation.md#onfinish)**(): [`MulticastDelegate`](mw.MulticastDelegate.md)<() => `void`\>  |
| 动画播放结束时(在动画不被中断且正常播放完成情况下)执行绑定函数。|
| **[slot](mw.Animation.md#slot)**(): [`AnimSlot`](../enums/mw.AnimSlot.md)  |
| 设置动画播放插槽|
| **[speed](mw.Animation.md#speed)**(): `number`  |
| 设置动画的播放速率|

### Methods <Score text="Methods" /> 
| **[pause](mw.Animation.md#pause)**(): `boolean`  |
| :-----|
| 暂停动画|
| **[play](mw.Animation.md#play)**(): `boolean`  |
| 播放动画。从动画资源的起点播放动画。生效范围与角色创建方式绑定。|
| **[resume](mw.Animation.md#resume)**(): `boolean`  |
| 恢复播放动画|
| **[stop](mw.Animation.md#stop)**(): `boolean`  |
| 停止播放动画|

## Accessors

### assetId <Score text="assetId" /> 

<table class="get-set-table">
<thead><tr>
<th style="text-align: left">

• `get` **assetId**(): `string` 

</th>
</tr></thead>
<tbody><tr>
<td style="text-align: left">


获取动画资源ID。目前是动画资源在编辑器左侧栏中，由美术创作者上传，鼠标指向可看到动画的GUID。

之后会开启开发者上传其制作的动画资源通道，将其上传到MW编辑器后，可以使用自己上传的动画资源。


#### Returns

| `string` |  |
| :------ | :------ |

</td>
</tr></tbody>
</table>

___

### isPlaying <Score text="isPlaying" /> 

<table class="get-set-table">
<thead><tr>
<th style="text-align: left">

• `get` **isPlaying**(): `boolean` 

</th>
</tr></thead>
<tbody><tr>
<td style="text-align: left">


是否播放


::: warning Precautions

是否播放，true表示动画对象的正在播放，false表示动画对象未播放。

:::


#### Returns

| `boolean` |  |
| :------ | :------ |

</td>
</tr></tbody>
</table>

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_IsPlaying"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_IsPlaying extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```
___

### length <Score text="length" /> 

<table class="get-set-table">
<thead><tr>
<th style="text-align: left">

• `get` **length**(): `number`

</th>
</tr></thead>
<tbody><tr>
<td style="text-align: left">


获取动画时长。当前动画对象中关联的动画的时长以秒为单位。


#### Returns

| `number` |  |
| :------ | :------ |

</td>
</tr></tbody>
</table>

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_Length"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_Length extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```
___

### loop <Score text="loop" /> 

<table class="get-set-table">
<thead><tr>
<th style="text-align: left">

• `get` **loop**(): `number` 

</th>
<th style="text-align: left">

• `set` **loop**(`loopCount`): `void` 

</th>
</tr></thead>
<tbody><tr>
<td style="text-align: left">


获取动画播放循环次数。



#### Returns

| `number` |  |
| :------ | :------ |


</td>
<td style="text-align: left">


设置动画的播放循环次数.


#### Parameters

| `loopCount` | `number` |
| :------ | :------ |



</td>
</tr></tbody>
</table>

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_Loop"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_Loop extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```
___

### onFinish <Score text="onFinish" /> 

<table class="get-set-table">
<thead><tr>
<th style="text-align: left">

• `get` **onFinish**(): [`MulticastDelegate`](mw.MulticastDelegate.md)<() => `void`\> <Badge type="tip" text="client" />

</th>
</tr></thead>
<tbody><tr>
<td style="text-align: left">


播放结束委托。

动画播放结束时(在动画不被中断且正常播放完成情况下)执行绑定函数。


::: warning Precautions

性能限制，服务器不播放动画，仅客户端触发，请在客户端使用该委托。有几种情况下不会触发该委托 1 调用pause方法 2 调用stop方法 3 该动画正在播放，调用play接口。

:::


#### Returns

| [`MulticastDelegate`](mw.MulticastDelegate.md)<() => `void`\> |  |
| :------ | :------ |

</td>
</tr></tbody>
</table>

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_OnFinish"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_OnFinish extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```
___

### slot <Score text="slot" /> 

<table class="get-set-table">
<thead><tr>
<th style="text-align: left">

• `get` **slot**(): [`AnimSlot`](../enums/mw.AnimSlot.md)

</th>
<th style="text-align: left">

• `set` **slot**(`animslot`): `void`

</th>
</tr></thead>
<tbody><tr>
<td style="text-align: left">


获取动画播放插槽

#### Returns

| [`AnimSlot`](../enums/mw.AnimSlot.md) |  |
| :------ | :------ |


</td>
<td style="text-align: left">


设置动画播放插槽

#### Parameters

| `animslot` | [`AnimSlot`](../enums/mw.AnimSlot.md) |
| :------ | :------ |



</td>
</tr></tbody>
</table>

___

### speed <Score text="speed" /> 

<table class="get-set-table">
<thead><tr>
<th style="text-align: left">

• `get` **speed**(): `number` 

</th>
<th style="text-align: left">

• `set` **speed**(`speed`): `void` 

</th>
</tr></thead>
<tbody><tr>
<td style="text-align: left">


获取动画的播放速率


::: warning Precautions

设置播放速率(动画切换时有融合时间,动画太短，当speed=1时 动画可能不明显) ,数值无范围限制，速率的符号表示播放方向，正表示正向播放，
负表示逆向播放, speed为1表示原始速率,默认值为2。设置该值不会改变播放的起点.

:::


#### Returns

| `number` |  |
| :------ | :------ |


</td>
<td style="text-align: left">


设置动画的播放速率


::: warning Precautions

设置播放速率(动画切换时有融合时间,动画太短，当speed=1时 动画可能不明显) ,数值无范围限制，速率的符号表示播放方向，正表示正向播放，
负表示逆向播放, speed为1表示原始速率,默认值为1。设置该值不会改变播放的起点.

:::

#### Parameters

| `speed` | `number` |
| :------ | :------ |

</td>
</tr></tbody>
</table>

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_Speed"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_Speed extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```


## Methods

### pause <Score text="pause" /> 

• **pause**(): `boolean` 

暂停动画

#### Returns

| `boolean` | 暂停结果 |
| :------ | :------ |


::: warning Precautions

不会触发onFinish委托。生效范围与角色创建方式绑定。

:::

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_Pause"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_Pause extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```

___

### play <Score text="play" /> 

• **play**(): `boolean` 

播放动画。从动画资源的起点播放动画。生效范围与角色创建方式绑定。

#### Returns

| `boolean` | 播放结果 |
| :------ | :------ |


<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_Play"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_Play extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```

___

### resume <Score text="resume" /> 

• **resume**(): `boolean` 

恢复播放动画

#### Returns

| `boolean` | 继续结果 |
| :------ | :------ |


::: warning Precautions

从当前位置继续动画播放。生效范围与角色创建方式绑定。

:::

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_Resume"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_Resume extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```

___

### stop <Score text="stop" /> 

• **stop**(): `boolean` 

停止播放动画

#### Returns

| `boolean` | 停止结果 |
| :------ | :------ |


::: warning Precautions

不触发动画结束回调。生效范围与角色创建方式绑定。

:::

<p style="font-size: 14px;"> 使用示例:将使用到的资源:"14700,20380"拖入优先加载栏。创建一个名为"Example_Animation_Stop"的脚本,放置在对象栏中,打开脚本,输入以下代码保存,运行游戏,在玩家角色上加载舞蹈动画,并修改循环次数为10，播放速度为2倍。给【动画完成】委托添加函数，播放一个升级特效。按下键盘“1”, 开始播放动画.按下键盘“2”, 暂停播放动画.按下键盘“3”, 继续播放动画.按下键盘“4”, 停止播放动画.代码如下: </p>

```ts
@Component
export default class Example_Animation_Stop extends Script {
    // 当脚本被实例后，会在第一帧更新前调用此函数
    protected onStart(): void {
        // 下列代码仅在客户端执行
        if(SystemUtil.isClient()) {
            // 获取当前客户端玩家
            let myPlayer = Player.localPlayer;
            // 获取玩家控制角色
            let myCharacter = myPlayer.character;
            // 给角色加载一个舞蹈动画
            let danceAnimation = myCharacter.loadAnimation("14700");
            // 动画的属性
            console.log("动画时长 " + danceAnimation.length);
            // 循环播放10次
            danceAnimation.loop = 10;
            // 2倍播放速度
            danceAnimation.speed = 2;
            // 给【动画完成】委托添加函数，播放一个升级特效
            danceAnimation.onFinish.add(() => {
                EffectService.playOnGameObject("20380", myCharacter, {slotType: HumanoidSlotType.Root});
            });
            // 添加一个按键方法:按下键盘“1”，开始播放
            InputUtil.onKeyDown(Keys.One, () => {
                danceAnimation.play();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“2”，暂停播放
            InputUtil.onKeyDown(Keys.Two, () => {
                danceAnimation.pause();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“3”，继续播放
            InputUtil.onKeyDown(Keys.Three, () => {
                danceAnimation.resume();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
            // 添加一个按键方法:按下键盘“4”，停止播放
            InputUtil.onKeyDown(Keys.Four, () => {
                danceAnimation.stop();
                console.log("动画播放 " + danceAnimation.isPlaying);
            });
        }
    }
}
```
