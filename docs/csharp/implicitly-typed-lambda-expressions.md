---
title: 隐式类型化 lambda 表达式
description: 了解为什么不能使用隐式类型化变量声明来声明 lambda 表达式。
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: f06c55f51c30c941d6d507ac8e2edd95c5152742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="implicitly-typed-lambda-expressions"></a>隐式类型化 lambda 表达式

我没有使用 `var` 声明此表达式树。 不能使用隐式类型化变量声明来声明 lambda 表达式。
它会对编译器造成循环逻辑问题。 `var` 声明会告知编译器通过赋值运算符右侧的表达式的类型查明变量的类型。 Lambda 表达式没有编译时类型，但是可转换为任何匹配委托或表达式类型。 将 lambda 表达式分配给委托或表达式类型的变量时，可告知编译器尝试并将 lambda 表达式转换为与“分配对象”变量的签名匹配的表达式或委托。 编译器必须尝试使赋值右侧的内容与赋值左侧的类型匹配。 

赋值两侧都无法告知编译器查看赋值运算符另一侧的对象并查看我的类型是否匹配。

通过阅读[这篇文章](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf)（PDF 下载），甚至可以获得有关 C# 语言为何指定该行为的详细信息


