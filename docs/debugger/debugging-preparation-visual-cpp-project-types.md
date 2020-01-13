---
title: Příprava na ladění projektů C++ | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: dc663115e98d7553e03a186874d59b75eb68cb90
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916310"
---
# <a name="debugging-preparation-c-project-types"></a>Příprava ladění: C++ typy projektů
Tato část popisuje, jak ladit základního projektu typy vytvořené [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] šablony projektu.

 Všimněte si, že tyto typy projektů, které vytvářejí knihovny DLL jako jejich výstup, byly seskupeny do [ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md) z důvodu běžné funkce sdílejí.

## <a name="BKMK_In_this_topic"></a> V tomto tématu
 [Doporučené nastavení vlastností](#BKMK_Recommended_Property_Settings)

 [Projekty Win32](#BKMK_Win32_Projects)

- [Chcete-li ladit aplikace jazyka C nebo C++ Win32](#BKMK_To_debug_a_C_or_C___Win32_application)

- [K ručnímu nastavení konfigurace ladění](#BKMK_To_manually_set_a_Debug_configuration)

  [Aplikace Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="BKMK_Recommended_Property_Settings"></a> Doporučené nastavení vlastností
 Určité vlastnosti měly být nastaveny stejným způsobem jako pro všechny nespravované ladění scénářů. Následující tabulky obsahují doporučené nastavení vlastností. Nastavení, které tu nejsou uvedené, mohou lišit mezi typy nespravovaného jiného projektu. Další informace najdete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Vlastnosti konfigurace &#124; C/C++ &#124; optimalizace uzlu

|Název vlastnosti|Nastavení|
|-------------------|-------------|
|**Optimalizace**|Nastavte na **zakázáno (/ 0 d).** Optimalizovaný kód je těžší ladit, protože generované pokyny neodpovídají přímo ke zdrojovému kódu. Pokud zjistíte, váš program obsahuje chybu, která se zobrazí pouze v optimalizovaném kódu, můžete zapnout toto nastavení, ale mějte na paměti, že kód zobrazený v **zpětný překlad** okna je generován z optimalizovaného zdrojového, který se nemusí shodovat, co vidíte ve zdroji systém Windows. Další funkce, jako je například krokování, nemusí chovat dle očekávání.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Vlastnosti konfigurace &#124; Linkeru &#124; uzlu ladění

|Název vlastnosti|Nastavení|
|-------------------|-------------|
|**Generovat ladicí informace**|Vždy byste měli nastavit tuto možnost na **Ano (/ DEBUG)** vytvořit ladicí symboly a soubory potřebné pro ladění. Když aplikace přejde do produkčního prostředí, můžete nastavit na vypnuto.|

 [V tomto tématu](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Win32_Projects"></a> Projekty Win32
 Win32 – aplikace se tradiční Windows programy napsané v jazyce C nebo C++. Ladění tohoto typu aplikace v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je jednoduché.

 Win32 – aplikace patří aplikace knihovny MFC a ATL projekty. Pomocí rozhraní Windows API a mohou používat knihovny MFC nebo ATL, ale nepoužívají common language runtime (CLR). Může, ale volání spravovaného kódu, který používá modul CLR.

 Následující postup vysvětluje, jak ladit projekt Win32 v rámci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dalším způsobem, jak ladit aplikaci Win32 je a spusťte tak aplikaci mimo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a připojit se k němu. Další informace najdete v tématu [připojení k běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Chcete-li ladit aplikace jazyka C nebo C++ Win32

1. Otevřete projekt v sadě Visual Studio.

2. Na **ladění** nabídce zvolte **Start**.

3. Ladění pomocí technik popsaných v [části první pohled na ladicí program](../debugger/debugger-feature-tour.md).

### <a name="BKMK_To_manually_set_a_Debug_configuration"></a> K ručnímu nastavení konfigurace ladění

1. Na **zobrazení** nabídky, klikněte na tlačítko **stránky vlastností**.

2. Klikněte na tlačítko **vlastnosti konfigurace** uzlu otevřete ho, pokud ještě není

3. Vyberte **Obecné**a nastavte hodnotu **výstup** řádku do **ladění**.

4. Otevřít **C/C++** uzel a vyberte možnost **Obecné**.

    V **ladění** řádek zadejte typ ladění informace generované kompilátorem. Je možné hodnoty zahrnují **databázi programu (/Zi)** nebo **databáze programu pro upravit a pokračovat (/ZI)** .

5. Vyberte **optimalizace**a **optimalizace** řádek, vyberte **zakázáno (/ 0d)** z rozevíracího seznamu.

    Optimalizovaný kód je těžší ladit, protože generované pokyny neodpovídají přímo ke zdrojovému kódu. Pokud zjistíte, že váš program obsahuje chybu, která se zobrazí pouze v optimalizovaném kódu, můžete zapnout toto nastavení, ale mějte na paměti, že kód zobrazený v okně zpětného překladu je generován z optimalizovaného zdrojového, který se nemusí shodovat se zobrazí ve zdrojových oknech. Funkce, jako je například krokování mohou zobrazit zarážky a provádění bodů nesprávně.

6. Otevřít **Linkeru** uzel a vyberte možnost **ladění**. V prvním **generovat** řádek, vyberte **Ano (/ DEBUG)** z rozevíracího seznamu. Vždy nastavte při ladění.

   Další informace najdete v tématu[nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [V tomto tématu](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Windows_Forms_Applications___NET_"></a> Aplikace Windows Forms (.NET)
 **Windows Forms aplikace (.NET)** šablona vytvoří [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikace Windows Forms. Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Ladění tohoto typu aplikace v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je podobná ve spravovaných aplikacích Windows Forms.

 Při vytváření projektu Windows Forms pomocí šablony projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky vytvoří požadované nastavení konfigurace Debug a Release. Pokud třeba, můžete změnit tato nastavení v  **\<název projektu > stránky vlastností** dialogové okno. Další informace najdete v tématu [konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md).

 Další informace najdete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Je další způsob, jak ladit aplikaci Windows Forms a spusťte tak aplikaci mimo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a připojit se k němu. Další informace najdete v tématu [připojení ke spuštění programu nebo více programů](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [V tomto tématu](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Viz také:
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Připojení ke spuštěnému programu nebo více programům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Konfigurace ladění a vydaných verzí](../debugger/how-to-set-debug-and-release-configurations.md)
- [Postupy: vytvoření projektu aplikace Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))