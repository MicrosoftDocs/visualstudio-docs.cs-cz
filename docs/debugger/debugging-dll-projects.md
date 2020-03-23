---
title: Ladění projektů DLL | Dokumenty společnosti Microsoft
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302201"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Ladění knihoven DLL v sadě Visual Studio (C#, C++, Visual Basic, F#)

Knihovna DLL (dynamická knihovna) je knihovna, která obsahuje kód a data, která může používat více než jedna aplikace. Pomocí sady Visual Studio můžete vytvářet, vytvářet, konfigurovat a ladit knihovny DLL.

## <a name="create-a-dll"></a>Vytvoření dll.

Následující šablony projektů sady Visual Studio mohou vytvářet knihovny DLL:

- Knihovna tříd Jazyka C#, Visual Basic nebo F#
- Knihovna jazyka C# nebo Visual Basic Windows Forms Control (WCF)
- Knihovna dynamických spojů jazyka C++ (DLL)

Další informace naleznete [v tématu Techniky ladění knihovny MFC](../debugger/mfc-debugging-techniques.md).

Ladění knihovny WCF je podobné ladění knihovny tříd. Podrobnosti naleznete v tématu [Windows Forms Controls](/dotnet/framework/winforms/controls/index).

Obvykle voláte dll z jiného projektu. Při ladění volajícího projektu, v závislosti na konfiguraci DLL, můžete krok do a ladění kódu DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Konfigurace ladění dll

Když k vytvoření aplikace použijete šablonu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu Visual Studia, automaticky vytvoří požadovaná nastavení pro konfigurace sestavení ladění a vydání. V případě potřeby můžete tato nastavení změnit. Další informace najdete v těchto článcích:

- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Nastavení projektu pro konfigurace ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Postup: Nastavení konfigurací ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Nastavit atribut ladění jazyka C++

Aby se ladicí program mohl připojit k dll c++ `DebuggableAttribute`, musí kód C++ vyzařovat .

**Nastavení `DebuggableAttribute`:**

1. Vprůzkumníka **řešení** vyberte projekt DLL jazyka C++ a vyberte ikonu **Vlastnosti,** nebo klepněte pravým tlačítkem myši na projekt a vyberte **vlastnosti**.

1. V podokně **Vlastnosti** vyberte v části Ladění propojovacího **zařízení** > **Debugging** **možnost Ano (/ASSEMBLYDEBUG)** pro **ladicí sestavení**.

Další informace naleznete v tématu [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>Nastavení umístění souborů DLL c/c++

Chcete-li ladit externí dll, volající projekt musí být schopen najít DLL, jeho [soubor .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)a všechny ostatní soubory, které vyžaduje DLL. Můžete vytvořit vlastní úlohu sestavení, která tyto soubory zkopíruje * \<do složky projektu>\Debug* output folder, nebo můžete soubory zkopírovat ručně.

U projektů c/c++ můžete nastavit umístění souborů záhlaví a LIB na stránkách vlastností projektu, místo toho, abyste je zkopírovali do výstupní složky.

**Nastavení umístění záhlaví c/c++ a souboru LIB:**

1. Vprůzkumníka **řešení** vyberte projekt DLL c/c/c++ a vyberte ikonu **Vlastnosti,** nebo klepněte pravým tlačítkem myši na projekt a vyberte **vlastnosti**.

1. V horní části podokna **Vlastnosti** vyberte v části **Konfigurace**možnost **Všechny konfigurace**.

1. V části **C/C++** > **Obecné** > **další zahrnutí adresářů**zadejte složku, která má soubory hlaviček.

1. V **části Propojovací** > **obecné** > **další knihovny adresáře**, zadejte složku, která má lib soubory.

1. V části Další závislosti > **linkeru** > **Additional Dependencies**zadejte úplnou cestu a název souboru LIB. **Linker**

1. Vyberte **OK**.

Další informace o nastavení projektu jazyka C++ najdete v [tématu Odkaz na stránku vlastnosti systému Windows C++](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Vytvoření verze ladění

Ujistěte se, že sestavení verze ladění DLL před zahájením ladění. Chcete-li ladit dll, volající aplikace musí být schopen najít svůj [soubor .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) a všechny ostatní soubory, které vyžaduje DLL.

Můžete vytvořit vlastní úlohu sestavení pro kopírování souborů DLL do * \<volající složky projektu>\Debug* output folder, nebo můžete soubory zkopírovat ručně.

Nezapomeňte volat dll ve správném umístění. To se může zdát zřejmé, ale pokud volající aplikace najde a načte jinou kopii DLL, ladicí program nikdy nenarazí na zarážky, které nastavíte.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Ladění dll

DLL nelze spustit přímo. Musí být volána aplikací, obvykle souborem *EXE.* Další informace naleznete v tématu [Projekty sady Visual Studio – C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Chcete-li ladit dll, můžete [spustit ladění z volající aplikace](#vxtskdebuggingdllprojectsthecallingapplication)nebo ladění z projektu [DLL](how-to-debug-from-a-dll-project.md) zadáním jeho volání aplikace. Můžete také použít okno [okamžité](#vxtskdebuggingdllprojectstheimmediatewindow) ladicího programu k vyhodnocení funkcí nebo metod dll v době návrhu bez použití volající aplikace.

Další informace naleznete [v tématu První pohled na ladicí program](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Zahájení ladění z volající aplikace

Aplikace, která volá dll může být:

- Aplikace z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu ve stejném nebo jiném řešení než DLL.
- Existující aplikace, která je již nasazená a spuštěná v testovacím nebo produkčním počítači.
- Nachází se na webu a má přístup prostřednictvím adresy URL.
- Webová aplikace s webovou stránkou, která vkládá dll.

Chcete-li ladit dll z volající aplikace, můžete:

- Otevřete projekt pro volající aplikaci a začněte ladit výběrem **ladění ladění** > **sstartovat** nebo stisknutím **klávesy F5**.

  – nebo –

- Připojte se k aplikaci, která je již nasazená a spuštěná v testovacím nebo produkčním počítači. Tuto metodu použijte pro knihovny DLL na webech nebo ve webových aplikacích. Další informace naleznete v [tématu Postup: Připojení ke spuštěnému procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Než začnete ladit volající aplikaci, nastavte zarážku v DLL. Viz [Použití zarážek](../debugger/using-breakpoints.md). Při zásahu zarážky DLL, můžete krokovat kód, pozorování akce na každém řádku. Další informace naleznete [v tématu Navigace v kódu v ladicím programu](../debugger/navigating-through-code-with-the-debugger.md).

Během ladění můžete použít okno **Moduly** k ověření dll a *souborů EXE,* které aplikace načte. Chcete-li otevřít okno **Moduly,** vyberte při ladění **možnost Ladění** > **modulů systému****Windows** > . Další informace naleznete v [tématu How to: Use the Modules window](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Použití okna Okamžité

Okno **Okamžité** můžete použít k vyhodnocení funkcí nebo metod dll v době návrhu. Okno **Okamžité** hraje roli volající aplikace.

>[!NOTE]
>Můžete použít **okamžité** okno v době návrhu s většinou typů projektů. Není podporovánpro SQL, webové projekty nebo skript.

Chcete-li například otestovat metodu pojmenovanou `Test` ve třídě `Class1`:

1. Po otevření projektu DLL otevřete okno **Okamžité** výběrem **možnosti Ladění** > **systému Windows** > **Immediate** nebo stisknutím **klávesy Ctrl**+**Alt**+**I**.

1. Vytvořte instanci objektu typu `Class1` zadáním následujícího kódu C# do okna **Okamžité** a stisknutím **klávesy Enter**. Tento spravovaný kód funguje pro c# a visual basic, s příslušnými změnami syntaxe:

   ```csharp
   Class1 obj = new Class1();
   ```

   V c# musí být všechny názvy plně kvalifikované. Všechny metody nebo proměnné musí být v aktuálním oboru a kontextu, když se služba jazyka pokusí vyhodnotit výraz.

1. Za `Test` předpokladu, že trvá jeden `int` parametr, vyhodnoťte `Test` pomocí **okamžité** okno:

   ```csharp
   ?obj.Test(10);
   ```

   Výsledek se vytiskne v okně **Okamžité.**

1. Můžete pokračovat v `Test` ladění umístěním zarážky uvnitř a potom znovu vyhodnotit funkci.

   Zarážka bude přístupů a `Test`můžete krokovat . Po spuštění `Test`zbývá , ladicí program bude zpět v režimu návrhu.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Ladění ve smíšeném režimu

Můžete napsat volající aplikaci pro DLL ve spravovaném nebo nativním kódu. Pokud vaše nativní aplikace volá spravovanou dll a chcete ladit oba, můžete povolit spravované i nativní ladicí program ve vlastnostech projektu. Přesný proces závisí na tom, zda chcete spustit ladění z projektu DLL nebo projektu volající aplikace. Další informace naleznete v [tématu How to: Debug in mixed mode](../debugger/how-to-debug-in-mixed-mode.md).

Můžete také ladit nativní dll ze spravovaného volajícího projektu. Další informace naleznete v tématu [Ladění spravovaného a nativního kódu](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Viz také
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Příprava na ladění projektů jazyka C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Nastavení projektu pro konfigurace ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
