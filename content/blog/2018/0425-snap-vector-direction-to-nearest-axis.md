---
title: Snap vector direction to nearest axis.
summary:  I have this case when I need to get my character direction is snapped to the nearest axis.
description:  How to find snapped vector to the nearest axis in Unity3D or Godot Engine
date: 2018-04-25
tags:
    - gamedev
---

I have a case where I need to snap my character's direction to the nearest axis. It looks something like this.

![Imgur](https://i.imgur.com/iTCZXET.gif)

My solution is to identify the axis with the largest absolute value, set it to 1, and set the other axes to 0. I also retain the sign of the largest axis.

Example, we have **Vector3(-0.5f, 0.1f, 0)**. The snapped direction is Vector3(-1,0,0).

```csharp
Vector3 SnappedToNearestAxis(Vector3 direction){
    float x = Abs(direction.x);
    float y = Abs(direction.y);
    float z = Abs(direction.z);
    if (x > y &amp;&amp; x > z){
        return Vector3(Sign(direction.x),0,0);
    } else if (y > x && y > z){
        return Vector3(0,Sign(direction.y),0);
    } else {
        return Vector3(0,0,Sign(direction.z));
    }
}
```