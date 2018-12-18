---
title: Ladění projektů knihovny DLL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c00740b31e5b9d7cc5678bfc248e673a57e59ccf
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305309"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Ladění knihovny DLL v sadě Visual Studio (C#, C++, Visual Basic, F#)

Knihovny DLL (dynamic link library) je knihovna, která obsahuje kód a data, která mohou využívat více než jednu aplikaci. Můžete použít Visual Studio k vytvoření, sestavení, konfiguraci a ladění knihoven DLL. 

## <a name="create-a-dll"></a>Vytvoření knihovny DLL

Následující šablony projektů Visual Studio můžete vytvořit knihovny DLL:

- C#, Visual Basic nebo F# knihovna tříd 
- C#a Visual Basic Windows Forms Knihovna ovládacích prvků (WCF) 
- C++ dynamická knihovna (DLL)

Další informace najdete v tématu [techniky ladění MFC](../debugger/mfc-debugging-techniques.md).

Ladění knihovny WCF je podobné ladění knihovny tříd. Podrobnosti najdete v tématu [ovládacích prvků Windows Forms](/dotnet/framework/winforms/controls/index).  

Obvykle volání knihovny DLL z jiného projektu. Při ladění volajícího projektu, v závislosti na konfiguraci knihovny DLL, můžete krokovat s vnořením a ladit kód knihovny DLL. 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Konfigurace ladění knihoven DLL

Při použití šablony projektu sady Visual Studio k vytvoření nové aplikace, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky vytvoří požadované nastavení pro konfiguraci sestavení pro ladění a vydání. Tato nastavení můžete změnit v případě potřeby. Další informace najdete v následujících článcích:

- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Nastavení pro projektu C# konfiguraci ladění](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Postupy: Konfigurace nastavení Debug a Release](../debugger/how-to-set-debug-and-release-configurations.md)  
  
### <a name="set-c-debuggableattribute"></a>Sada C++ DebuggableAttribute

Aby ladicí program připojil ke knihovně DLL jazyka C++, musí generovat kód C++ `DebuggableAttribute`. 

**Chcete-li nastavit `DebuggableAttribute`:**

1. Vyberte projekt knihovny DLL v C++ v **Průzkumníka řešení** a vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. 
   
1. V **vlastnosti** podokně v části **Linkeru** > **ladění**vyberte **Ano (/ ASSEMBLYDEBUG)** pro  **Laditelné sestavení**. 

Další informace najdete v tématu [/assemblydebug](/cpp/build/reference/assemblydebug-add-debuggableattribute).  

### <a name="vxtskdebuggingdllprojectsexternal"></a> Nastavit umístění souboru knihovny DLL jazyka C/C++ 

Chcete-li ladit externí knihovny DLL, volání projekt musí být schopen najít knihovnu DLL, jeho [soubor typu .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)a všechny další soubory, pak vyžaduje knihovna DLL. Můžete vytvořit vlastního sestavení úlohu kopírování těchto souborů do vaší  *\<složky projektu > \Debug* výstupní složky, nebo můžete zkopírovat soubory existuje ručně.

Pro projekty C/C++ můžete nastavit hlavičky a knihovny LIB umístění souborů na stránkách vlastností projektu, místo jejich kopírování do výstupní složky. 

**Chcete-li nastavit C/C++ umístění souborů záhlaví a LIB:**

1. Vyberte projekt knihovny DLL jazyka C/C++ v **Průzkumníka řešení** a vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. 
   
1. V horní části **vlastnosti** podokně v části **konfigurace**vyberte **všechny konfigurace**.
   
1. V části **C/C++** > **Obecné** > **další adresáře souborů k zahrnutí**, zadejte složku obsahující soubory hlaviček.
   
1. V části **Linkeru** > **Obecné** > **další adresáře knihoven**, zadejte složku, která obsahuje soubory LIB. 
   
1. V části **Linkeru** > **vstup** > **Další závislosti**, zadejte úplnou cestu a název souboru pro soubory knihovny LIB.

1. Vyberte **OK**.

Další informace o nastavení projektu jazyka C++, naleznete v tématu [stránky vlastností (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Sestavení ladicí verze  

Ujistěte se, že jste před zahájením ladění sestavení ladicí verze knihovny DLL. Chcete-li ladit knihovnu DLL, volání aplikace musí být schopna najít jeho [soubor typu .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) a všechny další soubory, pak vyžaduje knihovna DLL. 

Můžete vytvořit vlastního sestavení úlohu kopírování souborů knihovny DLL do vaší  *\<volání složky projektu > \Debug* výstupní složky, nebo můžete zkopírovat soubory existuje ručně.

Ujistěte se, že volání knihovny DLL do správného umístění. To se může zdát zřejmé, ale pokud volající aplikace vyhledá a načte různé kopie knihovny DLL, ladicí program nikdy dosaženo zarážky, které jste nastavili. 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Proveďte ladění knihovny DLL  

Knihovnu DLL nelze spustit přímo. Musí být volána aplikací, obvykle *.exe* souboru. Další informace najdete v tématu [vytvořit a spravovat projekty v jazyce Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects). 

Chcete-li ladit knihovnu DLL, můžete [spuštění ladění z volající aplikace](#vxtskdebuggingdllprojectsthecallingapplication), nebo [ladění z projektu knihovny DLL](how-to-debug-from-a-dll-project.md) tak, že zadáte jeho volající aplikace. Můžete také použít ladicí program [podokna](#vxtskdebuggingdllprojectstheimmediatewindow) k vyhodnocení funkcí knihovny DLL nebo metody v době návrhu, bez použití volání aplikace.

Další informace najdete v tématu [Začínáme s ladicím programem](getting-started-with-the-debugger.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Spuštění ladění z volající aplikace

Aplikace, který volá knihovnu DLL může být:  
  
- Aplikace z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu ve stejné nebo jiné řešení z knihovny DLL.  
- Existující aplikace, který už je nasazená a běží v testovacím nebo produkčním počítači.  
- Nachází se na webu a přístup prostřednictvím adresy URL.  
- Webová aplikace s webovou stránku, která knihovnu DLL.  
  
Chcete-li ladit knihovnu DLL z volající aplikace, můžete:  
  
- Projekt pro volající aplikaci otevřít a spustit ladění tak, že vyberete **ladění** > **spustit ladění** nebo stiskněte **F5**.  

  or  

- Připojte k aplikaci, která je již nasazen a spuštěn v testovacím nebo produkčním počítači. Tuto metodu použijte pro knihovny DLL na webech nebo ve službě web apps. Další informace najdete v tématu [postupy: připojení ke spuštěnému procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Před zahájením ladění volající aplikace, nastavte zarážku v knihovně DLL. Zobrazit [pomocí zarážek](../debugger/using-breakpoints.md). Při dosažení zarážky knihovny DLL, můžete krokovat kód, sledování akce na každém řádku. Další informace najdete v tématu [vyhledání kódu v ladicím programu](../debugger/navigating-through-code-with-the-debugger.md).
  
Během ladění, můžete použít **moduly** okno ověření knihovny DLL a *.exe* soubory zatížení aplikace. Chcete-li otevřít **moduly** okně během ladění, **ladění** > **Windows** > **moduly**. Další informace najdete v tématu [postupy: použití okna moduly](../debugger/how-to-use-the-modules-window.md). 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Použijte příkazové podokno  

Můžete použít **okamžité** okna k vyhodnocení funkcí knihovny DLL nebo metody v době návrhu. **Okamžité** okno hraje roli aplikace pro volajícího. 

>[!NOTE]
>Můžete použít **okamžité** okno v době návrhu s většinu typů projektu. Není podporována pro skript, SQL a webové projekty.

Například chcete-li otestovat metodu s názvem `Test` ve třídě `Class1`:

1. Po otevření projektu knihovny DLL, otevřete **okamžité** okna tak, že vyberete **ladění** > **Windows** > **okamžité**nebo stiskněte **Ctrl**+**Alt**+**můžu**.  
   
1. Vytvoří instanci objektu typu `Class1` zadáním následujícího C# kód **okamžité** okno a stisknutím klávesy **Enter**. Tento spravovaný kód funguje pro C# a Visual Basic, s příslušnými změnami syntaxe:  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   V jazyce C# musí být všechny názvy plně kvalifikovaný. Jakékoli metody nebo proměnné musí být v aktuálním oboru a kontext jazyková služba se pokusí pro vyhodnocení výrazu.  
   
1. Za předpokladu, že `Test` má jednu `int` parametr, vyhodnotit `Test` pomocí **okamžité** okno:  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   Vytiskne výsledek v **okamžité** okna.  
   
1. Můžete pokračovat v ladění `Test` umístěním zarážky dovnitř a opakovaným vyhodnocením funkce.  
   
   Bude dosaženo zarážkou a můžete krokovat `Test`. Poté, co provádění opustí `Test`, ladicí program bude zpět v návrhovém režimu.

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Ladění ve smíšeném režimu  

Pro knihovny DLL ve spravované nebo nativní kód můžete psát volání aplikace. Pokud vaše nativní aplikace volá spravované knihovny DLL a chcete obojí ladit, můžete povolit spravovaný a nativní ladící ve vlastnostech projektu. Přesný postup závisí na, jestli chcete spustit ladění z projektu knihovny DLL nebo projekt volající aplikace. Další informace najdete v tématu [postupy: ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md). 

Můžete také ladit nativní knihovnu DLL ze spravovaného projektu volání. Další informace najdete v tématu [ladění spravovaného a nativního kódu](how-to-debug-managed-and-native-code.md). 

## <a name="see-also"></a>Viz také:  
 [Ladit spravovaný kód](../debugger/debugging-managed-code.md)   
 [Typy projektů Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#a typy projektů jazyka Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Nastavení pro projektu C# konfiguraci ladění](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)
