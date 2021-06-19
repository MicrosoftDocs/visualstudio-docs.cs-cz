---
title: Příprava na ladění model Windows Forms aplikací | Microsoft Docs
description: Podnikně přípravné kroky pro model Windows Forms aplikací vytvořených šablonou projektu model Windows Forms v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2181fe0b0189b0c0472f4d7cadd6a7c8e172a9b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387746"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Příprava na ladění: Formulářová aplikace Windows

Šablona model Windows Forms App vytvoří novou model Windows Forms aplikace. Ladění tohoto typu aplikace v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroji je jednoduché. Informace o vytvoření projektu tohoto typu najdete v tématu [Vytvoření aplikace Windows Form.](../ide/create-csharp-winform-visual-studio.md)

 Když vytvoříte projekt model Windows Forms pomocí šablony projektu, automaticky vytvoří požadovaná nastavení pro konfigurace ladění a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vydání. V případě potřeby můžete tato nastavení změnit. Tato nastavení je možné změnit v dialogovém **\<project name> okně Stránky** vlastností (**Můj projekt v** Visual Basic).

 Další informace najdete v tématu [Doporučené nastavení vlastností.](../debugger/managed-debugging-recommended-property-settings.md)

 Následující tabulka obsahuje další doporučené nastavení vlastností.

### <a name="configuration-properties-in-debug-tab"></a>Vlastnosti konfigurace na kartě Ladění

|**Název vlastnosti**|**Nastavení**|
|-----------------------|-----------------|
|**Spustit akci**|- Většinu času **nastavte na** Start project (Spustit projekt). Pokud chcete **spustit jiný spustitelný soubor** při spuštění ladění (obvykle pro ladění knihoven DLL), nastavte možnost Spustit externí program.|

 Můžete ladit model Windows Forms aplikace z uvnitř nebo připojením k již [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spuštěné aplikaci. Další informace o připojení najdete v tématu [Připojení ke spuštěných procesům.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Ladění jazyka C#, F# nebo Visual Basic model Windows Forms aplikace

1. Otevřete projekt v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

2. Podle potřeby vytvořte zarážky.

    Protože model Windows Forms aplikace řízené událostmi, zarážek přechádí kód obslužné rutiny události nebo do metod, které volá kód obslužné rutiny události. Mezi typické události, ve kterých se mají umístit zarážky, patří:

   1. Události přidružené k ovládacímu prvku, například Kliknutí, Enter atd.

   2. Události související se spuštěním a vypnutím aplikace, jako je například Načtení, Aktivováno atd.

   3. Události zaměření a ověřování.

      Další informace najdete v tématu [Vytváření obslužných rutin událostí v model Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. V nabídce **Ladit** klikněte na **Spustit.**

4. Ladění pomocí technik probírané v [části První pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>Viz také
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Postupy: Nastavení konfigurací ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md)
- [Nastavení projektu pro konfigurace ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci Visual Basic ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)