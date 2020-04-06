---
title: Přehled automatizačních modelů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710012"
---
# <a name="automation-model-overview"></a>Přehled modelu automatizace
Model automatizace se skládá ze sady objektů, proti kterým můžete napsat doplněk nebo rozšíření sady Visual Studio. Doplněk je aplikace, která může manipulovat s prostředím sady Visual Studio a automatizovat běžné úlohy. Rozšíření sady Visual Studio můžete vytvořit vlastní součásti sady Visual Studio nebo přidat do funkce standardních součástí, jako je například textový editor.

## <a name="objects-in-the-automation-model"></a>Objekty v modelu automatizace
 Model automatizace se skládá ze souvisejících skupin objektů, které řídí hlavní aspekty společného prostředí. Následující diagram znázorňuje rozsáhlou sadu objektů sady Visual Studio, které tvoří model automatizace.

 ![Graf objektů automatizace sady Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectGraf")

 Další informace naleznete [v tématu Rozšíření prostředí sady Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).

 Prostředí poskytuje model pro různé funkční oblasti. Například je model kódu pro různé prvky, které můžete najít v kódu. K dispozici je model dokumentu pro různé prvky dokumentu. Jedna oblast, oblast projektu, je obzvláště zajímavá pro poskytovatele VSPackage. Pravděpodobně budete chtít, aby nové typy projektů přispívat k [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelu [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] automatizace v podstatě stejným způsobem jako a přispět k modelu automatizace. Tento proces je popsán v [poskytnout automatizaci pro VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).

 Místa, kde můžete zvážit rozšíření modelu automatizace prostředí:

- Project

- Dokument

- kód

- Sestavení

Další informace o automatizaci naleznete v [tématu Automatizace a rozšiřitelnost pro Visual Studio](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015). Tento dokument a dokumenty, které poskytuje odkazy na, vám pomohou při rozhodování o tom, jak byste měli poskytnout automatizaci pro váš VSPackage.

## <a name="see-also"></a>Viz také
- [Postup: Vytvoření doplňku](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
