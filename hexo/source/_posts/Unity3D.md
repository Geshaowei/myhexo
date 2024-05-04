---
title: Unity3D
date: 2024-03-23 13:42:47
tags: 2D游戏开发
---
关于2D横板序列帧动画游戏开发记录，重点技术涉及：2D精灵图片切割，Animation序列帧动画生成，Animator动画管理。基础UI设计，事件绑定，键盘事件监听，刚体组件加碰撞体触发器的使用。

# 2D横板+像素+动作+闯关游戏设计

免费素材使用，重点使用2D序列帧动画

## 精灵图片切割要点

图片像素需要根据原始像素进行切割，注意质量要原版质量.

## 键盘监听事件

inputsystem的使用以及跳跃事件和键盘使用的绑定。

## Animation动画制作

首先创造Animator 进行动画管理，然后找到Animation动画制作pattle，根据面板进行创建，要点在于每秒多少帧，调节这个可以帮助动画的流畅度设计。

## Animator动画切换管理

Animator是动画的逻辑切换判断，在2D像素风格中，首先要做的就是把切换的等待设置为0，不适用动画切换等待，之后的就是设计每个动画的切换逻辑，特殊的在于触发器的使用，触发器是触发一次变转化一次动作。

还有一个要点是动画管理的脚本尽量单独使用，方便管理。

动画还可以设置多个管理层，有覆盖和优先级的设定，下面的weight要调整至1，防止被覆盖。《跳跃+攻击不在一个面板的话需要这样设置，以免不会同时调用》

## 事件的绑定 UnityEvent

Unity 自带了一套事件绑定方法，使用UnityEvent头文件，生成的事件为Public，可以直接在Unity编辑器中进行拖拽绑定，然后使用.来进行调用这一系列事件，事件可以由多个方法组成，可以传入参数，使用的时候利用? 来检查时候有绑定的方法，以免报错。

## Rigbody2D+Collision 刚体加碰撞体

刚体组件使得物体有了物理性质，碰撞体使得物体有了可以碰撞的条件。碰撞体可以点击Is Trigger 选项，使之成为触发器，这样可以用于检测碰撞或者接触到一定范围的物体。

## IEnumerator name 协程的使用

```C#
IEnumerator Onhurt(Vector2 dir)
{
    rb.AddForce(dir * hurtForce, ForceMode2D.Impulse);
    yield return new WaitForSeconds(0.45f);
    isHurt = false;
}
//调用
StartCoroutine(Onhurt(dir));
```

## UI设计

锚点的绑定。

##场景切换
利用了GameScenceSo的方法
currentLoadedScence.sceneReference.LoadSceneAsync(LoadSceneMode.Additive);

## 游戏进度的存储

ISaveable 接口的设计，实现Savedata 和Loaddata

Dictionary字典

保存数据Data 类

DataDefination设计字典存储物品的ID以及相关数值

DataManager的设计，单例模式，List保存DataDefination类。循环遍历并且加载数据。

JsonUtility.ToJson，序列化存储对象。

JsonUtility,FromJsonOverWrite(SceneToScave,newScene); 反序列化加载

//URL-packges: com.unity/nuget.newtonsoft-json     Newtonsoft Json
