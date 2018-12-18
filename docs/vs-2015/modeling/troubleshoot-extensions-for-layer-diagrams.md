---
title: Řešení potíží s rozšířeními pro diagramy vrstev | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6361651672e72df6661f030a4b6c8e451fdaea89
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738778"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Řešení potíží s rozšířeními pro diagramy vrstev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma řeší některé problémy, které se mohou vyskytnout při vytváření rozšíření modelu vrstvy.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Po stisknutí klávesy F5 pro ladění mého rozšíření, mé příkazy, obslužné rutiny gesta, rozšíření ověřování nebo vlastní vlastnosti se nezobrazí v diagramech vrstev v experimentální instanci aplikace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1. Otevřete řešení rozšíření v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]a na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**.  
  
2. Stisknutím klávesy **F5** nebo **CTRL + F5** spustit experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Otevřete diagram vrstvy a otestujte rozšíření.  
  
   V případě potřeby, pokračujte dalším postupem.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Běží stará verze mého rozšíření.  
  
1. Ujistěte se, že žádná experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] běží.  
  
2. Odstraňte následující složku: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [verze]  
  
   > [!NOTE]
   >  % LocalAppData % je obvykle *DriveName*: \Users\\*uživatelské jméno*\AppData\Local.  
  
   V případě potřeby, pokračujte dalším postupem.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Zobrazí se stará verze mých výsledků ověření nebo má metoda ověřování není volána.  
  
1.  V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**. Tato akce smaže zachycené výsledky předchozí analýzy ověření.  
  
2.  Ujistěte se, že jsou spojeny s prvky kódu vrstvy v modelu a modelu je alespoň jeden odkaz závislosti. Ověření není vyvolána, pokud není co ověřovat.  
  
3.  Pravidelné zarážky nemusí fungovat v metodě ověření, protože běží v samostatném procesu. Je nutné vložit volání `System.Diagnostics.Debugger.Launch()` Pokud chcete procházet metodou.  
  
4.  V **source.extension.vsixmanifest** ve vrstvě projektu ověřování, ujistěte se, že jste přidali **Komponenta MEF** položky a **vlastní typ rozšíření** položku **Obsahu**.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření diagramů vrstev](../modeling/extend-layer-diagrams.md)



