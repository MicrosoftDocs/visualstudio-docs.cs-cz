---
title: Přizpůsobení souborů projektu vytvořených pomocí VSTU | Microsoft Docs
description: Naučte se přizpůsobit soubory projektu vytvořené pomocí Visual Studio Tools for Unity (VSTU). Zkontrolujte příklad kódu jazyka C#.
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879314"
---
# <a name="customize-project-files-created-by-vstu"></a>Přizpůsobení souborů projektu vytvořených pomocí VSTU
Unity poskytuje zpětná volání během generování souboru projektu. Implementujte `OnGeneratedSlnSolution` metody a a `OnGeneratedCSProject` použijte [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) k úpravě souboru projektu nebo řešení, kdykoli je znovu vygenerován.

## <a name="demonstrates"></a>Demonstruje
Jak přizpůsobit soubory projektu sady Visual Studio vygenerované Visual Studio Tools for Unity.

## <a name="example"></a>Příklad

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
