---
title: Vytváření vlastních zobrazení spravovaných objektů | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3d75193368188efc660391d1e80c562ed881324b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578039"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Vytváření vlastních zobrazení spravovaných objektů (C#, Visual Basic, F#, C++/CLI)
Můžete přizpůsobit způsob, jakým aplikace Visual Studio zobrazuje datové typy v oknech proměnných ladicího programu.

## <a name="attributes"></a>Atributy

V C#, Visual Basic, F#a C++ (C++pouze kód/CLI), můžete přidat rozšíření pro vlastní data pomocí <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> a <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

V kódu .NET Framework 2,0 Visual Basic nepodporuje atribut DebuggerBrowsable. Toto omezení je odebráno v novějších verzích rozhraní .NET.

## <a name="visualizers"></a>Vizualizéry

Můžete napsat Vizualizér pro zobrazení libovolného spravovaného datového typu. Další informace naleznete v tématu [How to: Write a Vizualizér](/visualstudio/debugger/create-custom-visualizers-of-data).

> [!NOTE]
> Pro C++ kód můžete přidat rozšíření vlastních typů dat pomocí rozhraní Natvis, jak je popsáno v tématu [Vytvoření vlastních zobrazení C++ objektů v ladicím programu](/visualstudio/debugger/create-custom-views-of-native-objects).

## <a name="see-also"></a>Viz také

- [Řekněte ladicímu programu, co se má zobrazit pomocí atributu DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md)
- [Sdělte ladicímu programu, jaký typ se má zobrazit s použitím atributu používání DebuggerTypeProxy.](../debugger/using-debuggertypeproxy-attribute.md)
- [Okna Kukátko a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md)
- [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
