---
title: Řešení potíží s rozšířeními pro diagramy vrstev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658479"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Řešení potíží s rozšířeními pro diagramy vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma řeší některé problémy, se kterými se můžete setkat při vytváření rozšíření modelů vrstev.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Když stisknete klávesu F5 k ladění rozšíření, moje příkazy, obslužné rutiny gest, ověřovací rozšíření nebo vlastní vlastnosti se nezobrazí v diagramech vrstev v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Otevřete řešení rozšíření v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a v nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.

2. Stisknutím klávesy **F5** nebo **CTRL + F5** spusťte experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Otevřete diagram vrstev a otestujte rozšíření.

   V případě potřeby pokračujte dalším postupem.

#### <a name="an-old-version-of-my-extension-runs"></a>Spustí se stará verze mého rozšíření.

1. Ujistěte se, že není spuštěná žádná experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Odstraňte následující složku:%LocalAppData%\Microsoft\VisualStudio \\ [verze] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData% je obvykle *jednotka*: \Users \\*username*\AppData\Local.

   V případě potřeby pokračujte dalším postupem.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Zobrazí se stará verze mých výsledků ověření nebo metoda moje ověření není volána.

1. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] klikněte v nabídce **sestavení** na příkaz **Vyčistit řešení**. Tím se vymaže výsledky předchozí analýzy ověření v mezipaměti.

2. Ujistěte se, že vrstvy v modelu jsou spojeny s prvky kódu a že v modelu existuje alespoň jeden odkaz závislost. Ověřování není vyvoláno, pokud není k dispozici žádný k ověření.

3. Pravidelné zarážky nemusí fungovat v metodě ověřování, protože se spouští v samostatném procesu. Pokud chcete projít metodu, musíte do `System.Diagnostics.Debugger.Launch()` vložit volání.

4. V projektu **source. extension. vsixmanifest** v projektu ověření vrstvy Ujistěte se, že jste přidali položku **součásti MEF** a **vlastní položku typu rozšíření** v části **obsah**.

## <a name="see-also"></a>Viz také
 [Rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md)
