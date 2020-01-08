---
title: Chyby Návrháře tříd
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc8b2c013a3e685a6071f4a12d63e3ca475051a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596512"
---
# <a name="class-designer-errors"></a>Chyby Návrháře tříd

**Návrhář tříd** nesleduje umístění zdrojových souborů, takže úprava struktury projektu nebo přesunutí zdrojových souborů v projektu může způsobit, že **Návrhář tříd** ztratí sledování typu, například je běžné měnit typ zdroje typu typedef, základní třídy a typy přidružení. Může se zobrazit chyba, například **Návrhář tříd není možné zobrazit tento typ**. Chcete-li chybu vyřešit, přetáhněte změněný nebo znovu umístěný zdrojový kód do diagramu tříd a zobrazte jej.

## <a name="resources"></a>Prostředky

Pomoc s dalšími chybami a upozorněními najdete v následujících zdrojích informací:

- [Práce s vizuálním C++ kódem](working-with-visual-cpp-code.md) obsahuje informace o řešení C++ problémů, které se zobrazují v diagramu tříd.
- [Fórum sady Visual Studio Návrhář tříd](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner) nabízí fórum pro otázky týkající se **Návrhář tříd**.

## <a name="see-also"></a>Viz také:

- [Návrh a zobrazení tříd a typů](designing-and-viewing-classes-and-types.md)
