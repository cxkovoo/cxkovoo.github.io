---
title: Three.js Journey 学习笔记（一）：基础场景搭建与核心概念
date: 2026-04-22 14:21:11 +0800
categories: [THREEJS-JOURNEY]
tags: [threejs]
---

# Three.js Journey 学习笔记（一）：基础场景搭建与核心概念

最近开始系统学习 Three.js，跟着 Bruno Simon 的 Three.js Journey 课程一步步实践，收获非常多。这一系列文章主要用来记录学习过程、踩坑经验和关键知识点，方便自己回顾，也希望能帮到同样在入门 Three.js 的同学。

## 一、Three.js 核心三要素

任何一个 Three.js 应用，都离不开最基础的三个对象：

1. **Scene（场景）**
   相当于一个容器，存放所有物体、灯光、相机等。

2. **Camera（相机）**
   决定视角、视野和观察位置，常用 `PerspectiveCamera`。

3. **Renderer（渲染器）**
   将相机视角下的场景渲染到 Canvas 上。

## 二、最简 Three.js 场景代码

一个最基础的 Three.js 示例结构如下：

```javascript
import * as THREE from 'three'

// 场景
const scene = new THREE.Scene()

// 物体
const geometry = new THREE.BoxGeometry(1, 1, 1)
const material = new THREE.MeshBasicMaterial({ color: 0xff0000 })
const mesh = new THREE.Mesh(geometry, material)
scene.add(mesh)

// 相机
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight)
camera.position.z = 3
scene.add(camera)

// 渲染器
const renderer = new THREE.WebGLRenderer()
renderer.setSize(window.innerWidth, window.innerHeight)
document.body.appendChild(renderer.domElement)

// 渲染
renderer.render(scene, camera)
