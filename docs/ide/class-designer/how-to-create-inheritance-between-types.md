---
title: 'Postupy: vytvoření dědičnosti mezi typy (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8151020294f4fd5574a1de886509c5b11f0a326
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956676"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Postupy: vytvoření dědičnosti mezi typy v Návrháři tříd

Chcete-li vytvořit vztah dědičnosti mezi dvěma typy na diagram třídy pomocí **návrhář tříd**, základní typ připojení s jeho odvozený typ nebo typy. Můžete mít vztah dědičnosti mezi dvěma třídami, mezi třídy a rozhraní nebo mezi dvě rozhraní.

## <a name="to-create-an-inheritance-between-types"></a>Chcete-li vytvořit dědičnosti mezi typy

1.  Z projektu v **Průzkumníku**, otevřete soubor třídy diagram (.cd).

     Pokud nemáte diagramu tříd, vytvořte ho. V tématu [postupy: Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md).

2.  V **sada nástrojů**v části **návrhář tříd**, klikněte na tlačítko **dědičnosti**.

3.  Na diagramu tříd kreslení řádku s dědičnosti mezi typy, které chcete, od:

    -   Odvozené třídy za účelem základní třídy

    -   Implementující třídu rozhraní implementované

    -   Rozšíření rozhraní rozšířené rozhraní

4.  Případně pokud máte odvozený typ od obecného typu, klikněte na řádek dědičnosti. V **vlastnosti** nastavte **argumenty typu** vlastnost, která má odpovídat typ, který chcete použít pro obecný typ.

    > [!NOTE]
    > Pokud nadřazená abstraktní třída obsahuje nejméně jeden člen abstraktní, jsou implementované všechny abstraktní členy jako dědičných neabstraktní třídy.
    >
    >  I když můžete vizualizovat existující obecné typy, nelze vytvořit nové obecné typy. Parametry typu pro existující obecné typy také nelze změnit.

## <a name="see-also"></a>Viz také

- [Dědičnost](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Základní informace o dědičnosti](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Postupy: zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Třídy jazyka Visual C++ v Návrháři tříd](visual-cpp-classes.md)