---
title: Ladit projekty knihovny DLL | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315067"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Ladit knihovny DLL v aplikaci Visual Studio (C#, C++, Visual Basic, F #)

Knihovna DLL (dynamická knihovna) je knihovna, která obsahuje kód a data, která lze použít více než jednou aplikací. Pomocí sady Visual Studio můžete vytvářet, sestavovat, konfigurovat a ladit knihovny DLL.

## <a name="create-a-dll"></a>Vytvoření knihovny DLL

Následující šablony projektů sady Visual Studio mohou vytvořit knihovny DLL:

- Knihovna tříd C#, Visual Basic nebo F #
- Knihovna jazyka C# nebo Visual Basic model Windows Forms Control (WCF)
- Knihovna DLL (Dynamic-Link Library) C++

Další informace naleznete v tématu [techniky ladění knihovny MFC](../debugger/mfc-debugging-techniques.md).

Ladění knihovny WCF je podobné ladění knihovny tříd. Podrobnosti najdete v tématu [model Windows Forms Controls](/dotnet/framework/winforms/controls/index).

Obvykle je volána knihovna DLL z jiného projektu. Při ladění volajícího projektu v závislosti na konfiguraci knihovny DLL můžete krokovat a ladit kód knihovny DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Konfigurace ladění DLL

Při použití šablony projektu sady Visual Studio k vytvoření aplikace [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky vytvoří požadované nastavení pro konfiguraci ladění a sestavení. V případě potřeby můžete tato nastavení změnit. Další informace najdete v následujících článcích:

- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Postupy: nastavení konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Nastavení DebuggableAttribute C++

Aby se ladicí program připojil k knihovně DLL jazyka C++, musí generovat kód C++ `DebuggableAttribute` .

**Nastavit `DebuggableAttribute` :**

1. Vyberte projekt C++ DLL v **Průzkumník řešení** a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem myši na projekt a vyberte možnost **vlastnosti**.

1. V podokně **vlastnosti** v části ladění **linkeru**  >  **Debugging**vyberte **Ano (/ASSEMBLYDEBUG)** pro **Laditelné sestavení**.

Další informace najdete v tématu [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Nastavit umístění souborů DLL jazyka C/C++

Chcete-li ladit externí knihovnu DLL, volající projekt musí být schopný najít knihovnu DLL, její [soubor. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)a všechny další soubory, které knihovna DLL vyžaduje. Můžete vytvořit vlastní úlohu sestavení pro zkopírování těchto souborů do výstupní složky * \<project folder> \debug.* nebo můžete zkopírovat soubory ručně.

Pro projekty C/C++ můžete nastavit umístění souborů hlaviček a LIB na stránkách vlastností projektu místo jejich kopírování do výstupní složky.

**Chcete-li nastavit hlavičku C/C++ a umístění souborů LIB:**

1. Vyberte projekt knihovny DLL jazyka C/C++ v **Průzkumník řešení** a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem na projekt a vyberte možnost **vlastnosti**.

1. V horní části podokna **vlastností** vyberte v části **Konfigurace**možnost **všechny konfigurace**.

1. V části Obecné další adresáře k zahrnutí v **C/C++**  >  **General**  >  **Additional Include Directories**určete složku, která obsahuje soubory hlaviček.

1. V části **linker**  >  **Obecné**  >  **Další adresáře knihoven**zadejte složku, která obsahuje soubory LIB.

1. V části **linker**  >  **vstup**  >  **Další závislosti**zadejte úplnou cestu a název souboru pro soubory LIB.

1. Vyberte **OK**.

Další informace o nastavení projektu C++ naleznete v tématu [Referenční dokumentace stránky vlastností Windows c++](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Sestavení ladicí verze

Než začnete s laděním, nezapomeňte sestavit ladicí verzi knihovny DLL. Chcete-li ladit knihovnu DLL, volající aplikace musí být schopna najít [soubor. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) a všechny další soubory, které knihovna DLL vyžaduje.

Můžete vytvořit vlastní úlohu sestavení ke zkopírování souborů DLL do výstupní složky * \<calling project folder> \debug.* nebo můžete zkopírovat soubory ručně.

Ujistěte se, že je knihovna DLL volána ve správném umístění. To se může zdát zřejmé, ale pokud volající aplikace najde a načte jinou kopii knihovny DLL, ladicí program nikdy neobjeví zarážky, které jste nastavili.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ladění knihovny DLL

Knihovnu DLL nelze spustit přímo. Musí ji volat aplikace, obvykle soubor *. exe* . Další informace naleznete v tématu [projekty sady Visual Studio – C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Chcete-li ladit knihovnu DLL, můžete [Spustit ladění z volající aplikace](#vxtskdebuggingdllprojectsthecallingapplication)nebo [LADIT z projektu knihovny DLL](how-to-debug-from-a-dll-project.md) zadáním jeho volající aplikace. Můžete také použít [okno](#vxtskdebuggingdllprojectstheimmediatewindow) ladicího programu pro vyhodnocení funkcí DLL nebo metod v době návrhu bez použití volající aplikace.

Další informace najdete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Spustit ladění z volající aplikace

Aplikace, která volá knihovnu DLL, může být:

- Aplikace z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu ve stejném nebo jiném řešení než knihovna DLL.
- Existující aplikace, která je už nasazená a spuštěná v testovacím nebo produkčním počítači.
- Umístěný na webu a k němu se přistupoval prostřednictvím adresy URL.
- Webová aplikace s webovou stránkou, která vloží knihovnu DLL.

Chcete-li ladit knihovnu DLL z volající aplikace, můžete:

- Otevřete projekt pro volající aplikaci a spusťte ladění výběrem **ladění**  >  **Spustit ladění** nebo stisknutím klávesy **F5**.

  nebo

- Připojte se k aplikaci, která je už nasazená a spuštěná v testovacím nebo produkčním počítači. Tuto metodu použijte pro knihovny DLL na webech nebo ve webových aplikacích. Další informace najdete v tématu [Postup: připojení ke spuštěnému procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Než začnete ladit volající aplikaci, nastavte zarážku v knihovně DLL. Viz [použití zarážek](../debugger/using-breakpoints.md). Když je dosaženo zarážky knihovny DLL, můžete krokovat kód a pozorovat akci na každém řádku. Další informace naleznete v tématu [Navigace v kódu v ladicím programu](../debugger/navigating-through-code-with-the-debugger.md).

Během ladění můžete pomocí okna **moduly** ověřit knihovny DLL a soubory *. exe* , které aplikace načítá. Chcete-li otevřít okno **moduly** , při ladění vyberte možnost **ladit**  >  **moduly systému Windows**  >  **Modules**. Další informace najdete v tématu [Postupy: použití okna moduly](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Použít příkazové okno

Můžete použít **okamžité** okno k vyhodnocení funkcí knihoven DLL nebo metod v době návrhu. **Příkazové** okno hraje roli volající aplikace.

>[!NOTE]
>Můžete použít **okamžité** okno v době návrhu a většinu typů projektů. Pro SQL, webové projekty ani skripty se nepodporuje.

Chcete-li například testovat metodu s názvem `Test` ve třídě `Class1` :

1. Otevřete projekt knihovny DLL a otevřete okno **okamžité** , a to tak, že kliknete na tlačítko **ladění**  >  **oken**  >  **přímo** nebo stiskněte **klávesu CTRL** + **ALT +** + **I**.

1. Vytvořte instanci objektu typu tak, že do příkazového `Class1` okna zadáte následující **Immediate** kód jazyka C# a stisknete klávesu **ENTER**. Tento spravovaný kód funguje pro C# a Visual Basic s odpovídajícími změnami syntaxe:

   ```csharp
   Class1 obj = new Class1();
   ```

   V jazyce C# musí být všechny názvy plně kvalifikované. Pokud se služba jazyka pokusí vyhodnocení výrazu, musí být všechny metody a proměnné v aktuálním oboru a kontextu.

1. Za předpokladu, že `Test` přijímá jeden `int` parametr, se vyhodnotí pomocí příkazového `Test` **podokna** :

   ```csharp
   ?obj.Test(10);
   ```

   Výsledek se vytiskne v **příkazovém** okně.

1. Můžete pokračovat v ladění `Test` tak, že do něj zadáte zarážku a pak funkci vyhodnocujete znovu.

   Zarážka bude dosaženo a můžete krokovat `Test` . Po spuštění zůstane `Test` ladicí program zpátky v režimu návrhu.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Ladění ve smíšeném režimu

Můžete napsat volající aplikaci pro knihovnu DLL ve spravovaném nebo nativním kódu. Pokud vaše nativní aplikace volá spravovanou knihovnu DLL a chcete ladit obojí, můžete povolit spravované i nativní ladicí programy ve vlastnostech projektu. Přesný proces závisí na tom, zda chcete spustit ladění z projektu knihovny DLL nebo projektu volání aplikace. Další informace najdete v tématu [Postup: ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).

Nativní knihovnu DLL můžete také ladit ze spravovaného volajícího projektu. Další informace najdete v tématu [Postup ladění spravovaného a nativního kódu](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Viz také
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Příprava na ladění projektů C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Typy projektů jazyka C#, F # a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
