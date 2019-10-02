---
title: Vytváření vlastních zobrazení objektů | Microsoft Docs
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
ms.openlocfilehash: 36e875bc8101bc8a1b0eb1bec6671c76e3b0c9b2
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814302"
---
# <a name="create-custom-views-of-objects-c-visual-basic-f-ccli"></a>Vytváření vlastních zobrazení objektů (C#, Visual Basic, F#, C++/CLI)
Můžete přizpůsobit způsob, jakým aplikace Visual Studio zobrazuje datové typy v oknech proměnných ladicího programu.

## <a name="attributes"></a>Atributy

V C#, Visual Basic, F#a C++ (C++pouze kód/CLI), můžete přidat rozšíření pro vlastní data pomocí <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> a <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

V kódu .NET Framework 2,0 Visual Basic nepodporuje atribut DebuggerBrowsable. Toto omezení je odebráno v novějších verzích .NET Framework.

## <a name="visualizers"></a>Vizualizéry

Můžete napsat Vizualizér pro zobrazení libovolného spravovaného datového typu. Další informace najdete v tématu [jak: Napište Vizualizér @ no__t-0.

> [!NOTE]
> Pro C++ kód můžete přidat rozšíření vlastních typů dat pomocí rozhraní Natvis, jak je popsáno v tématu [Vytvoření vlastních zobrazení C++ objektů v ladicím programu](/visualstudio/debugger/create-custom-views-of-native-objects).

## <a name="see-also"></a>Viz také

- [Řekněte ladicímu programu, co se má zobrazit pomocí atributu DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md)
- [Sdělte ladicímu programu, jaký typ se má zobrazit s použitím atributu používání DebuggerTypeProxy.](../debugger/using-debuggertypeproxy-attribute.md)
- [Okna Kukátko a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md)
- [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)