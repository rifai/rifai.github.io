---
title: "Third person camera on Godot"
description:  "Exploring Third-Person Shooters: A Guide to Creating a Third-Person Camera with Godot"
summary: The third-person shooter genre is undeniably popular in the world of gaming.
date: 2023-09-28
tags:
    - godot
    - gamedev
---
The third-person shooter genre is undeniably popular in the world of gaming. To help you dive into this exciting genre, I've made a simple boilerplate code that demonstrates how to create a third-person camera using Godot, the powerful open source game engine.

```gdscript
extends Camera3D


@export 
var _target:Node3D # your character

@export
var _rotation_speed:float = 0.003 #height above target

@export
var _limit_x:float = 60 # in degree

var _current_rot:Vector3
var _distance:float = 15

func _ready():
    _current_rot = rotation
    var desired_position = _target.global_position + (quaternion * Vector3(0, 0, _distance))
    global_position = desired_position
    _show_pointer(false)

func _input(event):
    if _target == null:
        return
        
    if event is InputEventMouseMotion:
        var input_pos = event.relative
        _update_rotation(input_pos.x * _rotation_speed, input_pos.y * _rotation_speed)

func _update_rotation(input_x:float, input_y:float):
    var rotation_x = _current_rot.x - input_y
    var limit = deg_to_rad(_limit_x)

    _current_rot.x = clampf(rotation_x, -limit, limit)
    _current_rot.y = _current_rot.y - input_x;

    rotation = _current_rot
    var desired_position = _target.global_position + (quaternion * Vector3(0, 0, _distance))

    global_position = desired_position

func _show_pointer(show_pointer:bool):
    if show_pointer:
        Input.set_mouse_mode(Input.MOUSE_MODE_VISIBLE)
    else:
        Input.set_mouse_mode(Input.MOUSE_MODE_CAPTURED)
```

You can access the code and resources [here](https://github.com/rifai/godot-boilerplate). 

But that's not all - my commitment to your game development journey goes beyond this code. In the future, I'll continue to expand this resource with the most common game features and Godot capabilities. This will serve as a valuable repository for all your reusable game development needs.

