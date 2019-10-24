---
title: Příprava na ladění aplikací model Windows Forms | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ff927e5b917834341e442afa00e4acad4af2d2f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738102"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Příprava na ladění: Formulářová aplikace Windows
Šablona projektu model Windows Forms vytvoří aplikaci model Windows Forms. Ladění tohoto typu aplikace v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je jednoduché. Další informace naleznete v tématu [Vytvoření projektu aplikace pro systém Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Při vytváření projektu model Windows Forms se šablonou projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky vytvoří požadované nastavení pro ladění a vydání. V případě potřeby můžete tato nastavení změnit. Tato nastavení se dají změnit v dialogovém okně **\<project název > stránky vlastností** (**můj projekt** v Visual Basic).

 Další informace najdete v tématu [Nastavení Doporučené vlastnosti](../debugger/managed-debugging-recommended-property-settings.md).

 V následující tabulce je uvedeno jedno další nastavení Doporučené vlastnosti.

### <a name="configuration-properties-in-debug-tab"></a>Vlastnosti konfigurace na kartě ladění

|**Název vlastnosti**|**Nastavením**|
|-----------------------|-----------------|
|**Spustit akci**|-Nastavte na hodnotu **spustit projekt, a** to ve většinu času. Nastavte na **spustit externí program** , pokud chcete spustit další spustitelný soubor při spuštění ladění (obvykle pro ladění knihoven DLL).|

 Můžete ladit model Windows Forms aplikace zevnitř [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nebo připojením k již spuštěné aplikaci. Další informace o připojení najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Ladění aplikace C#, F#nebo Visual Basic model Windows Forms

1. Otevřete projekt v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. V případě potřeby vytvořte zarážky.

    Vzhledem k tomu, že aplikace model Windows Forms jsou založené na událostech, vaše zarážky budou přecházet do kódu obslužné rutiny události nebo do metod volaných kódem obslužné rutiny události. Mezi obvyklé události, do kterých se mají umístit zarážky, patří:

   1. Události přidružené k ovládacímu prvku, jako je například Click, ENTER atd.

   2. Události spojené s spuštěním a vypnutím aplikace, jako je například Load, aktivované atd.

   3. Události fokusu a ověření.

      Další informace naleznete v tématu [vytváření obslužných rutin událostí v model Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. V nabídce **ladit** klikněte na tlačítko **Start**.

4. Ladění pomocí technik popsaných v [části první pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>Viz také:
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Postupy: Nastavení konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)