---
title: Visual C++ IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 173020a95977bdae2ad3006ce23dea376fb9d22e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608825"
---
# <a name="visual-c-intellisense"></a>Visual C++ IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio 2015 je technologie IntelliSense k dispozici pro soubory s jedním kódem a také pro soubory v projektech. V projektech pro různé platformy jsou některé funkce IntelliSense k dispozici v souborech. cpp a. c v projektu se sdíleným kódem, i když jste v kontextu Androidu nebo iOS.

## <a name="intellisense-features-in-c"></a>Funkce IntelliSense vC++
 IntelliSense je název, který je dán pro sadu funkcí, které usnadňují kódování. Vzhledem k tomu, že různí lidé mají různé nápady na to, co je praktické, je prakticky možné povolit nebo zakázat všechny funkce IntelliSense na stránce **textový editor, CC++/, Upřesnit** vlastnosti.

 ![Nástroje, možnosti, textový editor, c&#47;c&#43;&#43;, Upřesnit](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")

 K přístupu k IntelliSense můžete použít položky nabídky a klávesové zkratky uvedené na následujícím obrázku.

 ![Visual c++&#43; &#43; – nabídka IntelliSense](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")

### <a name="statement-completion-and-member-list"></a>Dokončování příkazů a seznam členů
 Při psaní klíčového slova, typu, funkce, názvu proměnné nebo jiného prvku programu, který kompilátor rozpozná, Editor nabízí příkaz pro dokončení slova.

 Seznam ikon a jejich význam naleznete v tématu [zobrazení tříd a prohlížeč objektů ikony](../ide/class-view-and-object-browser-icons.md).

 ![Okno dokončení&#43; &#43; Wordu v jazyce Visual c++](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")

 První seznam členů, který je vyvolán, zobrazí pouze členy, kteří jsou k dispozici pro aktuální kontext. Pokud použijete **kombinaci kláves CTRL + J** , zobrazí se všichni členové bez ohledu na přístupnost. Pokud ji vyvoláte třetí, zobrazí se ještě širší seznam prvků programu. Doplňování příkazů můžete vypnout na stránce **Možnosti C/C++ obecné** .

 ![Seznam členů&#43; &#43; Visual C](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Help – parametr
 Když zadáte levou složenou závorku volání funkce nebo lomené závorky v deklaraci proměnné šablony třídy, editor zobrazí malé okno s typy parametrů pro každé přetížení funkce nebo konstruktoru. Parametr Current – založený na umístění kurzoru – je tučné. Doplňování příkazů můžete vypnout na stránce **Možnosti C/C++ obecné** .

 ![Visual c++&#43; &#43; – Help – parametr](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Rychlé informace
 Při najetí ukazatele myši na proměnnou se zobrazí malé okno s vložením, které zobrazuje informace o typu a záhlaví, ve kterém je typ definován. Pokud chcete zobrazit signaturu funkce, najeďte myší na volání funkce. Rychlé informace můžete vypnout na stránce **textový editor, CC++/, Upřesnit** .

 ![Visual C&#43; &#43; QuickInfo](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")

## <a name="error-squiggles"></a>Chyba vlnovek
 Vlnovky pod prvkem programu (proměnná, klíčové slovo, složené závorky, název typu atd.) volají upozornění na chybu nebo potenciální chybu v kódu. Při psaní dopředné deklarace se zobrazí zelená vlnovka, aby bylo možné připomenout, že je stále potřeba napsat implementaci. Fialová vlnovka se zobrazí ve sdíleném projektu, pokud dojde k chybě v kódu, který není aktuálně aktivní, například při práci v kontextu systému Windows, ale zadejte něco, co by bylo v kontextu Androidu chyba. Červená vlnovka značí chybu kompilátoru nebo upozornění v aktivním kódu, který je třeba zabývat.

 ![Vlnová&#43; &#43; Chyba jazyka Visual C](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")

## <a name="code-colorization-and-fonts"></a>Zabarvení kódu a písma
 Výchozí barvy a písma lze změnit pomocí stránky vlastností **prostředí, písma a barvy** . Můžete změnit písma pro mnoho oken uživatelského rozhraní, nikoli jenom Editor. Nastavení, která jsou specifická pro C++ začátek s "C++"; Ostatní nastavení platí pro všechny jazyky.

## <a name="cross-platform-intellisense"></a>IntelliSense pro různé platformy
 V projektu se sdíleným kódem jsou k dispozici některé funkce IntelliSense, jako jsou například vlnovky, i když pracujete v kontextu Androidu. Pokud napíšete kód, který by způsobil chybu v neaktivním projektu, IntelliSense stále zobrazuje vlnovky, ale mají jinou barvu než vlnovky pro chyby v aktuálním kontextu.

 Tady je aplikace OpenGL, která je nakonfigurovaná pro vývoj pro Android a iOS. Na ilustraci se zobrazuje upravovaný sdílený kód. V prvním obrázku je Android aktivním projektem:

 ![Projekt pro Android je aktivní projekt.](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")

 Všimněte si následujícího:

- Větev #else na řádku 8 je zobrazena šedě, aby označovala neaktivní oblast, protože `__ANDROID__` je definována pro projekt pro Android.

- Proměnná pozdravu na řádku 11 je inicializována s identifikátorem HELLo, který má fialovou vlnovkou. Důvodem je to, že v aktuálně neaktivním projektu iOS není definovaný žádný identifikátor HELLo. V případě Androidu na řádku 11 by se kompilace v iOS nepoužila. Vzhledem k tomu, že se jedná o sdílený kód, to je něco, co byste měli změnit, i když se zkompiluje v aktuálně aktivní konfiguraci.

- Řádek 12 obsahuje červenou vlnovku u identifikátoru BYE; Tento identifikátor není definován v aktuálně vybraném aktivním projektu.

  Nyní Změňte aktivní projekt na iOS. StaticLibrary a Všimněte si, jak se změní vlnovkou.

  ![pro iOS je vybraný jako aktivní projekt.](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

  Všimněte si následujícího:

- Větev #ifdef na řádku 6 je zobrazena šedě, protože je označena jako neaktivní oblast, protože pro projekt iOS není definováno \_ *\\ _ANDROID* .

- Proměnná pozdravu na řádku 11 se inicializuje s identifikátorem HELLo, který teď má červenou vlnovku. Důvodem je to, že v aktuálně aktivním projektu iOS není definován žádný identifikátor HELLo.

- Řádek 12 obsahuje fialovou vlnovkou na identifikátoru BYE; Tento identifikátor není definovaný v aktuálně neaktivním projektu Android. NativeActivity.

## <a name="single-file-intellisense"></a>IntelliSense s jedním souborem
 Když otevřete jeden soubor mimo libovolný projekt, budete mít i nadále IntelliSense. Můžete povolit nebo zakázat konkrétní funkce pomocí příkazu **textový editor, CC++/, Upřesnit** a zapnout nebo vypnout funkce technologie IntelliSense. Pro konfiguraci technologie IntelliSense pro samostatné soubory, které nejsou součástí projektu, hledejte **IntelliSense a procházení pro neprojektové soubory** v části **Upřesnit** . Podívejte se na téma [Průvodce vizuální C++ seznámení](https://msdn.microsoft.com/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).

 ![IntelliSense s&#43; &#43; jedním souborem v jazyce Visual c++](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")

 Ve výchozím nastavení používá technologie IntelliSense pro hledání hlavičkových souborů jenom standardní adresáře include. Chcete-li přidat další adresáře, otevřete místní nabídku v uzlu řešení a přidejte svůj adresář do seznamu **zdrojového kódu ladění** , jak ukazuje následující obrázek:

 ![Přidání cesty k souboru hlaviček.](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")

## <a name="see-also"></a>Viz také
 [Používání atributu IntelliSense](../ide/using-intellisense.md)
