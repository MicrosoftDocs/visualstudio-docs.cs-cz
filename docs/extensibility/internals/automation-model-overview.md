---
title: Přehled modelu automatizace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ea38dc79bd557f17bbae8276dd112304c9a40fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186732"
---
# <a name="automation-model-overview"></a>Přehled modelu automatizace
Model automatizace se skládá ze sady objektů, pro které můžete napsat doplněk nebo rozšíření sady Visual Studio. Doplněk je aplikace, která může pracovat s prostředím sady Visual Studio a automatizovat běžné úlohy. Rozšíření sady Visual Studio může vytvořit vlastní součásti sady Visual Studio nebo přidat funkce standardních komponent, jako je textový editor.

## <a name="objects-in-the-automation-model"></a>Objekty v modelu automatizace
 Model automatizace se skládá ze souvisejících skupin objektů, které řídí hlavní charakteristiky společného prostředí. Následující diagram znázorňuje rozsáhlou sadu objektů aplikace Visual Studio, které tvoří model automatizace.

 ![Graf automatizačních objektů sady Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Další informace najdete v tématu věnovaném [rozšiřování prostředí sady Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Prostředí poskytuje model pro různé funkční oblasti. Například existuje model kódu pro různé prvky, které mohou být v kódu nalezeny. Pro různé prvky dokumentu existuje model dokumentu. Jedna oblast, oblast projektu, má zvláštní význam pro poskytovatele VSPackage. Pravděpodobně budete chtít, aby vaše nové typy projektů přispívaly do modelu automatizace stejným způsobem jako [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] přispívají k modelu automatizace. Tento proces je popsaný v [tématech poskytnutí automatizace pro VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Místa, kde můžete zvážit rozšíření modelu automatizace prostředí:

- Project

- Dokument

- Kód

- Sestavení

Další informace o automatizaci najdete v tématu [Automatizace a rozšiřitelnost pro Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Tento dokument a dokumenty, na které poskytuje odkazy, vám pomůžou při rozhodování o tom, jak byste měli pro VSPackage vytvořit automatizaci.

## <a name="see-also"></a>Viz také:
- [Postupy: vytvoření doplňku](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)