---
title: Přehled modelu automatizace | Microsoft Docs
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
ms.openlocfilehash: aa06b58ccd8d4cba8e16b17bc725798ae02d7e8f
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414435"
---
# <a name="automation-model-overview"></a>Přehled modelu automatizace
Model automatizace se skládá ze sady objektů, pro které můžete napsat doplněk nebo rozšíření sady Visual Studio. Doplněk je aplikace, která může pracovat s prostředím sady Visual Studio a automatizovat běžné úlohy. Rozšíření sady Visual Studio může vytvořit vlastní součásti sady Visual Studio nebo přidat funkce standardních komponent, jako je textový editor.

## <a name="objects-in-the-automation-model"></a>Objekty v modelu automatizace
 Model automatizace se skládá ze souvisejících skupin objektů, které řídí hlavní charakteristiky společného prostředí. Následující diagram znázorňuje rozsáhlou sadu objektů aplikace Visual Studio, které tvoří model automatizace.

 ![Graf automatizačních objektů sady Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Další informace najdete v tématu věnovaném [rozšiřování prostředí sady Visual Studio](/previous-versions/esk3eey8(v=vs.140)).

 Prostředí poskytuje model pro různé funkční oblasti. Například existuje model kódu pro různé prvky, které mohou být v kódu nalezeny. Pro různé prvky dokumentu existuje model dokumentu. Jedna oblast, oblast projektu, má zvláštní význam pro poskytovatele VSPackage. Pravděpodobně budete chtít, aby vaše nové typy projektů přispívaly do modelu automatizace stejným způsobem jako [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] přispívat do modelu automatizace. Tento proces je popsaný v [tématech poskytnutí automatizace pro VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).

 Místa, kde můžete zvážit rozšíření modelu automatizace prostředí:

- Project

- Dokument

- Kód

- Sestavení

Další informace o automatizaci najdete v tématu [Automatizace a rozšiřitelnost pro Visual Studio](/previous-versions/visualstudio/visual-studio-2015/extensibility/extensibility-in-visual-studio?preserve-view=true&view=vs-2015). Tento dokument a dokumenty, na které poskytuje odkazy, vám pomůžou při rozhodování o tom, jak byste měli pro VSPackage vytvořit automatizaci.

## <a name="see-also"></a>Viz také
- [Postupy: vytvoření doplňku](/previous-versions/80493a3w(v=vs.140))