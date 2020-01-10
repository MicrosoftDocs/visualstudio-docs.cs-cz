---
title: Další informace o chybách Návrhář tříd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a095cd909dcd4d378fddc91c9151cf28e34a8ee5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852212"
---
# <a name="additional-information-about-class-designer-errors"></a>Další informace o chybách návrháře tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář tříd nesleduje umístění zdrojových souborů, takže úprava struktury projektu nebo přesunutí zdrojových souborů v projektu může způsobit, že Návrhář tříd ztratí sledovat typ (zejména zdrojový typ typu typedef, základní třídy nebo typy přidružení). Může se zobrazit chyba, například **Návrhář tříd není možné zobrazit tento typ**. Pokud tak učiníte, znovu přetáhněte změněný nebo znovu umístěný zdrojový kód do diagramu tříd a znovu ho zobrazte.

 Pomoc s dalšími chybami a upozorněními najdete v následujících zdrojích informací:

 [Práce s vizuálním C++ kódem (návrhář tříd)](../ide/working-with-visual-cpp-code-class-designer.md) obsahuje informace o řešení C++ problémů, které se zobrazují v diagramu tříd.

 [Fórum sady Visual Studio Návrhář tříd](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1) Poskytuje fórum pro otázky týkající se Návrhář tříd.

## <a name="see-also"></a>Viz také
 [Navrhování a zobrazování tříd a typů](../ide/designing-and-viewing-classes-and-types.md)
