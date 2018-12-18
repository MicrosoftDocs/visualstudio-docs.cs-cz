---
title: Řešení potíží s rozšířeními pro diagramy závislostí
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8acde589ebf47d4a67609e847a84bd7c7acd8482
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899640"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Řešení potíží s rozšířeními pro diagramy závislostí

Toto téma řeší některé problémy, které se mohou vyskytnout při vytváření rozšíření modelu vrstvy.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>Po stisknutí klávesy F5 pro ladění mého rozšíření, mé příkazy, obslužné rutiny gesta, rozšíření ověřování nebo vlastní vlastnosti nejsou zobrazeny na diagramů závislostí v experimentální instanci sady Visual Studio

1. Otevřete řešení rozšíření v experimentální instanci sady Visual Studio a na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**.

2. Stisknutím klávesy **F5** nebo **CTRL + F5** spustit experimentální instanci sady Visual Studio. Otevřete diagram závislostí a otestujte rozšíření.

   V případě potřeby, pokračujte dalším postupem.

## <a name="an-old-version-of-my-extension-runs"></a>Běží stará verze mého rozšíření.

1. Ujistěte se, že je spuštěna žádná experimentální instance sady Visual Studio.

2. Odstraňte následující složku: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [verze]

   > [!NOTE]
   > % LocalAppData % je obvykle *DriveName*: \Users\\*uživatelské jméno*\AppData\Local.

   V případě potřeby, pokračujte dalším postupem.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Zobrazí se stará verze mých výsledků ověření nebo má metoda ověřování není volána.

1.  V experimentální instanci sady Visual Studio na **sestavení** nabídky, klikněte na tlačítko **Vyčistit řešení**. Tato akce smaže zachycené výsledky předchozí analýzy ověření.

2.  Ujistěte se, že jsou spojeny s prvky kódu vrstvy v modelu a modelu je alespoň jeden odkaz závislosti. Ověření není vyvolána, pokud není co ověřovat.

3.  Pravidelné zarážky nemusí fungovat v metodě ověření, protože běží v samostatném procesu. Je nutné vložit volání `System.Diagnostics.Debugger.Launch()` Pokud chcete procházet metodou.

4.  V **source.extension.vsixmanifest** ve vrstvě projektu ověřování, ujistěte se, že jste přidali **Komponenta MEF** položky a **vlastní typ rozšíření** položku **Obsahu**.

## <a name="see-also"></a>Viz také

- [Rozšíření diagramů závislostí](../modeling/extend-layer-diagrams.md)
