---
title: Vytváření vlastních zobrazení spravovaných objektů | Microsoft Docs
description: Ladicí program sady Visual Studio zobrazuje data v oknech proměnných. Naučte se přizpůsobit způsob, jakým se zobrazují datové typy, včetně vlastních typů.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c054d3bcfbb06d0093f04190ab8b4825b5cbf20f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865797"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Vytváření vlastních zobrazení spravovaných objektů (C#, Visual Basic, F #, C++/CLI)
Můžete přizpůsobit způsob, jakým aplikace Visual Studio zobrazuje datové typy v oknech proměnných ladicího programu.

## <a name="attributes"></a>Atributy

V jazyce C#, Visual Basic, F # a C++ (pouze kód C++/CLI), můžete přidat rozšíření pro vlastní data pomocí <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , <xref:System.Diagnostics.DebuggerDisplayAttribute> a <xref:System.Diagnostics.DebuggerBrowsableAttribute> .

V kódu .NET Framework 2,0 Visual Basic nepodporuje atribut DebuggerBrowsable. Toto omezení je odebráno v novějších verzích rozhraní .NET.

## <a name="visualizers"></a>Vizualizéry

Můžete napsat Vizualizér pro zobrazení libovolného spravovaného datového typu. Další informace naleznete v tématu [How to: Write a Vizualizér](create-custom-visualizers-of-data.md).

> [!NOTE]
> Pro kód jazyka C++ můžete přidat rozšíření vlastních datových typů pomocí architektury Natvis, jak je popsáno v tématu [Vytvoření vlastních zobrazení objektů C++ v ladicím programu](create-custom-views-of-native-objects.md).

## <a name="see-also"></a>Viz také

- [Řekněte ladicímu programu, co se má zobrazit pomocí atributu DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md)
- [Sdělte ladicímu programu, jaký typ se má zobrazit s použitím atributu používání DebuggerTypeProxy.](../debugger/using-debuggertypeproxy-attribute.md)
- [Okna Kukátko a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md)
- [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
