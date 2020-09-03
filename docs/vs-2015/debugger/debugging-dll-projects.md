---
title: Ladění projektů knihovny DLL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a4533c304f84d9dc59ec6b05328528870e49655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691389"
---
# <a name="debugging-dll-projects"></a>Ladění projektů knihovny DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V následujících šablonách jsou vytvořeny knihovny DLL:  
  
- (C++, C# a Visual Basic) Knihovna tříd  
  
- (C++, C# a Visual Basic): Knihovna ovládacích prvků model Windows Forms  
  
   Ladění knihovny ovládacích prvků systému Windows je podobné ladění projektu knihovny tříd. Ve většině případů budete volat ovládací prvek systému Windows z jiného projektu. Při ladění volajícího projektu můžete krokovat s kódem ovládacího prvku Windows, nastavit zarážky a provádět jiné operace ladění. Další informace naleznete v tématu [model Windows Forms Controls](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# a Visual Basic): knihovna webového ovládacího prvku  
  
   Další informace naleznete v tématu [Knihovna webového ovládacího prvku (spravovaný kód)](../debugger/web-control-library-managed-code.md).  
  
- (C++): ovládací prvek ActiveX knihovny MFC a ovládací prvek ActiveX inteligentního zařízení knihovny MFC  
  
   Ovládací prvky ActiveX jsou ovládací prvky, které se dají stáhnout přes Internet, do klientského počítače a zobrazovat a aktivovat na webových stránkách.  
  
   Ladění ovládacích prvků ActiveX je podobné ladění jiných druhů ovládacích prvků, protože nelze spustit jako samostatné, ale musí být vloženy do webové stránky HTML. Další informace naleznete v tématu [How to: Debug a Control ActiveX](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): knihovna DLL inteligentního zařízení MFC  
  
   Další informace naleznete v tématu [techniky ladění knihovny MFC](../debugger/mfc-debugging-techniques.md).  
  
  Tato část také obsahuje informace o následujících tématech:  
  
- [Postupy: Ladění z projektu knihovny DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Postupy: Ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md)  
  
  Toto téma obsahuje následující části, které obsahují informace o tom, jak připravit na ladění knihoven tříd:  
  
- [Sestavení ladicí verze](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Ladění ve smíšeném režimu](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Změna výchozích konfigurací](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Způsoby, jak ladit knihovnu DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [Volající aplikace](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Ovládací prvky na webové stránce](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [Příkazové okno](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
## <a name="building-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Sestavení ladicí verze  
 Bez ohledu na to, jak spouštíte ladění, ujistěte se, že nejprve sestavíte ladicí verzi knihovny DLL a zajistěte, aby byla ladicí verze v umístění, kde aplikace očekává, že ji najde. To se může zdát zřejmé, ale pokud tento krok zapomenete, aplikace může najít jinou verzi knihovny DLL a načíst ji. Program se pak bude nadále spouštět a přitom zajímá, proč vaše zarážka nikdy nedosáhla. Při ladění můžete ověřit, které knihovny DLL byl program načten, otevřením okna **moduly** ladicího programu. Okno **moduly** obsahuje všechny knihovny DLL nebo exe načtené v procesu, který ladíte. Další informace najdete v tématu [Postupy: použití okna moduly](../debugger/how-to-use-the-modules-window.md).  
  
 Aby ladicí program připojil kód napsaný v jazyce C++, musí kód generovat `DebuggableAttribute` . To můžete do kódu přidat automaticky tak, že propojíte s možností linkeru [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) .  
  
## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Ladění ve smíšeném režimu  
 Volající aplikace, která volá vaši knihovnu DLL, může být napsána ve spravovaném kódu nebo nativním kódu. Pokud je spravovaná knihovna DLL volána nativním kódem a chcete ladit obojí, spravované i nativní ladicí programy musí být povoleny. Tuto možnost můžete vybrat v dialogovém okně nebo v okně ** \<Project> vlastností** . Postup závisí na tom, zda jste spustili ladění z projektu knihovny DLL nebo projektu volání aplikace. Další informace najdete v tématu [Postup: ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).  
  
## <a name="changing-default-configurations"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Změna výchozích konfigurací  
 Při vytváření projektu konzolové aplikace se šablonou projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky vytvoří požadované nastavení pro ladění a vydání. V případě potřeby můžete tato nastavení změnit. Další informace naleznete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md), [nastavení projektu pro Visual Basic konfiguraci ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)a [Postup: nastavení konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md).  
  
## <a name="ways-to-debug-the-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Způsoby, jak ladit knihovnu DLL  
 Každý z projektů v této části vytvoří knihovnu DLL. Nemůžete spustit knihovnu DLL přímo; musí být volána aplikací, obvykle EXE. Další informace najdete v tématu [vytváření a správa Visual C++ch projektů](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). Volající aplikace může vyhovovat jednomu z následujících kritérií:  
  
- Aplikace vytvořená v jiném projektu ve stejném [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které obsahuje knihovnu tříd.  
  
- Existující aplikace již nasazená v testovacím nebo produkčním počítači.  
  
- Umístěný na webu a k němu se přistupoval prostřednictvím adresy URL.  
  
- Webová aplikace, která obsahuje webovou stránku, která vloží knihovnu DLL.  
  
### <a name="debugging-the-calling-application"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Ladění volající aplikace  
 Chcete-li ladit knihovnu DLL, začněte laděním volající aplikace, obvykle buď EXE nebo webová aplikace. Existuje několik způsobů, jak je ladit.  
  
- Pokud máte projekt pro volající aplikaci, můžete otevřít tento projekt a spustit provádění z nabídky **ladění** . Další informace naleznete v tématu [How to: Start Execution](https://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Pokud je volající aplikace existující program, který už je nasazený na testovacím nebo produkčním počítači a je už spuštěný, můžete se k němu připojit. Tuto metodu použijte, pokud je knihovna DLL ovládacím prvkem, který je hostován aplikací Internet Explorer, nebo ovládacím prvkem na webové stránce. Další informace najdete v tématu [Postup: připojení ke spuštěnému procesu](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- Můžete ho ladit z projektu knihovny DLL. Další informace naleznete v tématu [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).  
  
- Můžete ho ladit z příkazového [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **podokna** . V takovém případě přehraje **příkazové** okno roli aplikace.  
  
  Před zahájením ladění volající aplikace obvykle budete chtít nastavit zarážku v knihovně tříd. Další informace naleznete v tématu [zarážky a trasováním](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Při dosažení zarážky můžete krokovat kód a pozorovat akci na každém řádku, dokud neizolujete problém. Další informace najdete v tématu [Přehled krokování kódu](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
### <a name="controls-on-a-web-page"></a><a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Ovládací prvky na webové stránce  
 Chcete-li ladit ovládací prvek webové stránky, vytvořte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stránku, která jej vloží, pokud taková stránka ještě neexistuje. Pak umístěte zarážky do kódu webové stránky i kódu ovládacího prvku. Následně vyvoláte webovou stránku z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Před zahájením ladění volající aplikace obvykle budete chtít nastavit zarážku v knihovně DLL. Při dosažení zarážky můžete krokovat kód a pozorovat akci na každém řádku, dokud neizolujete problém. Další informace naleznete v tématu [zarážky a trasováním](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### <a name="the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Příkazové okno  
 Můžete vyhodnotit funkce nebo metody v knihovně DLL bez nutnosti volání aplikace. Provádíte ladění v době návrhu a použijete **okamžité** okno. Chcete-li tento postup ladit, proveďte následující kroky, zatímco je projekt knihovny DLL otevřený:  
  
1. Otevřete **příkazové** okno ladicího programu.  
  
2. Chcete-li otestovat metodu s názvem `Test` ve třídě `Class1` , vytvořte instanci objektu typu zadáním `Class1` následujícího kódu jazyka C# v příkazovém okně. Tento spravovaný kód funguje pro Visual Basic a C++ s odpovídajícími změnami syntaxe:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     V jazyce C# musí být všechny názvy plně kvalifikované. Kromě toho musí být všechny metody nebo proměnné v aktuálním oboru a kontextu relace ladění.  
  
3. Za předpokladu, že `Test` přijímá jeden `int` parametr, se vyhodnotí pomocí příkazového `Test` **podokna** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Výsledek bude vytištěn v **příkazovém** okně.  
  
4. Můžete pokračovat `Test` v ladění umístěním zarážky dovnitř a následnou vyhodnocením funkce:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Zarážka bude dosaženo a budete moci krokovat `Test` . Po spuštění zůstane `Test` ladicí program zpátky v režimu návrhu.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Visual C++ typy projektů](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Typy projektů jazyka C#, F # a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)
