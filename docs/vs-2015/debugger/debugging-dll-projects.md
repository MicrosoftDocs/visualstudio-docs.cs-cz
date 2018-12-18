---
title: Ladění projektů knihovny DLL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: c5177d7bd43a0bc1ba29778ba99cc891fd9f739b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792382"
---
# <a name="debugging-dll-projects"></a>Ladění projektů knihovny DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Následující šablony vytvoří knihovny DLL:  
  
- (C++, C# a Visual Basic) Knihovna tříd  
  
- (C++, C# a Visual Basic): Knihovna ovládacích prvků formulářů Windows  
  
   Ladění knihovny ovládacích prvků Windows je podobné ladění projektu knihovny tříd. Ve většině případů budete volat ovládací prvek Windows z jiného projektu. Při ladění volajícího projektu můžete krokovat s vnořením kódu ovládacího prvku Windows, nastavit zarážky a provádět jiné operace ladění. Další informace najdete v tématu [ovládacích prvků Windows Forms](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# a Visual Basic): Knihovna webových prvků  
  
   Další informace najdete v tématu [Knihovna webových prvků (spravovaný kód)](../debugger/web-control-library-managed-code.md).  
  
- (C++): ovládací prvek ActiveX knihovny MFC a knihovny MFC Smart zařízení ovládacího prvku ActiveX  
  
   Ovládací prvky ActiveX jsou ovládací prvky, které je možné stáhnout z Internetu do klientských počítačů a zobrazí a aktivují na webových stránkách.  
  
   Ladění ovládacích prvků ActiveX je podobné ladění jiných typů ovládacích prvků, protože nemůže být spuštěno samostatně, ale musí být vloženo na webové stránce HTML. Další informace najdete v tématu [postupy: ladění ovládacího prvku ActiveX](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): inteligentní zařízení knihovny DLL MFC  
  
   Další informace najdete v tématu [techniky ladění MFC](../debugger/mfc-debugging-techniques.md).  
  
  Tato část také obsahuje informace o následujících tématech:  
  
- [Postupy: Ladění z projektu knihovny DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Postupy: Ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md)  
  
  Toto téma obsahuje následující oddíly, které poskytují důležité informace o přípravě k ladění knihoven tříd:  
  
- [Sestavení ladicí verze](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Ladění ve smíšeném režimu](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Změna výchozí konfigurace](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Způsoby, jak ladit knihovnu DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [Volající aplikace](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Ovládací prvky na webové stránce](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [Příkazové podokno](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Sestavení ladicí verze  
 Bez ohledu na to, jak spouštíte ladění Ujistěte se, že nejprve sestavení ladicí verze knihovny DLL a ujistěte se, že ladicí verze je v umístění, kde se očekává, že aplikace ji najít. To se může zdát zřejmé, ale pokud zapomenete tento krok, aplikace může najít jinou verzi knihovny DLL a načíst ji. Program bude pokračovat spustit, zatímco se budete divit, proč vaší zarážky nikdy dosaženo. Když ladíte, můžete ověřit, které knihovny DLL váš program načetl, otevřením ladicího programu **moduly** okna. **Moduly** okno uvádí jednotlivé knihovny DLL nebo EXE načtené v procesu, který ladíte. Další informace najdete v tématu [postupy: použití okna moduly](../debugger/how-to-use-the-modules-window.md).  
  
 Aby ladicí program připojil kód napsaný v jazyce C++, musí kód generovat `DebuggableAttribute`. Můžete přidat to do kódu automaticky díky propojení s [/assemblydebug](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) – možnost linkeru.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Ladění ve smíšeném režimu  
 Volající aplikace, která volá vaši knihovnu DLL je možné psát v spravovaném kódu nebo nativním kódu. Pokud je vaše spravovaná knihovna DLL volána pomocí nativního kódu a chcete obojí ladit, spravované a nativní ladicí programy musí být povoleny. To můžete vybrat  **\<Projekt > stránky vlastností** nebo dialogovém okně. Postup závisí na tom, zda spustíte ladění z projektu knihovny DLL nebo projekt volající aplikace. Další informace najdete v tématu [postupy: ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Změna výchozí konfigurace  
 Když vytvoříte projekt konzolové aplikace pomocí šablony projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky vytvoří požadované nastavení konfigurace Debug a Release. V případě potřeby můžete změnit tato nastavení. Další informace najdete v tématu [nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [nastavení projektu pro ladění konfigurace jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md), [nastavení projektu pro konfiguraci ladění jazyka Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), a [postupy: Konfigurace nastavení ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Způsoby, jak ladit knihovnu DLL  
 Všechny projekty v této části vytvoří knihovnu DLL. Knihovnu DLL nelze spustit přímo. musí být volána aplikací, obvykle EXE. Další informace najdete v tématu [vytváření a správa projektů Visual C++](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). Volající aplikace mohou přizpůsobit některé z následujících kritérií:  
  
-   Aplikace vytvořené v jiném projektu ve stejném [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které obsahuje knihovnu tříd.  
  
-   Existující aplikace již nasazená v testovacím nebo produkčním počítači.  
  
-   Nachází se na webu a přístup prostřednictvím adresy URL.  
  
-   Webová aplikace, které obsahuje webovou stránku obsahující knihovnu DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Ladění volající aplikace  
 Chcete-li ladit knihovnu DLL, začněte laděním volající aplikace, obvykle buď aplikace EXE nebo webová aplikace. Existuje několik způsobů, jak ho ladit.  
  
- Pokud máte projekt pro volající aplikace, můžete otevřít tento projekt a spustit provádění z **ladění** nabídky. Další informace najdete v tématu [postupy: spuštění provádění](http://msdn.microsoft.com/en-us/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Pokud volající aplikace existující program již nasazený v testovacím nebo produkčním počítači a je již spuštěna můžete připojit k němu. Tuto metodu použijte, pokud je knihovna DLL kontrolovaně aplikace Internet Explorer nebo ovládacího prvku na webové stránce. Další informace najdete v tématu [postupy: připojení k procesu spuštění](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- Můžete ho ladit z projektu knihovny DLL. Další informace najdete v tématu [postupy: ladění z projektu knihovny DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
- Můžete ho ladit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **okamžité** okna. V takovém případě **okamžité** okno hraje roli aplikace.  
  
  Před zahájením ladění volající aplikace je obvyklé nastavit zarážku v knihovně tříd. Další informace najdete v tématu [zarážky a sledované body](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Při dosažení zarážky, můžete krokovat kód, sledování akce na každém řádku, dokud nebude problém. Další informace najdete v tématu [přehled krokování kódu](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
###  <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Ovládací prvky na webové stránce  
 Chcete-li ladit ovládací prvek webové stránky, vytvořte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stránka, která jej použije, pokud taková ještě stránka neexistuje. Pak umístěte zarážky v kódu webové stránky, jakož i kód ovládacího prvku. Poté vyvoláte webovou stránku z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Před zahájením ladění volající aplikace je obvyklé nastavit zarážku v knihovně DLL. Při dosažení zarážky, můžete krokovat kód, sledování akce na každém řádku, dokud nebude problém. Další informace najdete v tématu [zarážky a sledované body](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Příkazové podokno  
 Bez nutnosti volání aplikace můžete vyhodnotit funkce nebo metody v knihovně DLL. Proveďte ladění v době návrhu a použít **okamžité** okna. Chcete-li ladit tímto způsobem, proveďte tyto kroky při otevřeném projektu knihovny DLL:  
  
1.  Spusťte ladicí program **okamžité** okna.  
  
2.  Chcete-li otestovat metodu s názvem `Test` ve třídě `Class1`, vytvoří instanci objektu typu `Class1` zadáním následujícího kódu jazyka C# do okna příkazy. Tento spravovaný kód funguje pro Visual Basic a C++ s příslušnými změnami syntaxe:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     V jazyce C# musí být všechny názvy plně kvalifikovaný. Kromě toho jakékoli metody nebo proměnné musí být v aktuálním měřítku a kontextu relace ladění.  
  
3.  Za předpokladu, že `Test` má jednu `int` parametr, vyhodnotit `Test` pomocí **okamžité** okno:  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Výsledek bude vytištěn v **okamžité** okna.  
  
4.  Můžete pokračovat v ladění `Test` umístěním zarážky dovnitř a opakovaným vyhodnocením funkce:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Bude dosaženo zarážkou a budete moci krokovat `Test`. Poté, co provádění opustí `Test`, ladicí program bude zpět v návrhovém režimu.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Typy projektů Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Nastavení projektu pro jazyk C# konfiguraci ladění](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Konfigurace ladění projektu v jazyce Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)



