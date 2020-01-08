---
title: C++IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: c0d1be12f733a858bf223fb1dce6a091c0dc6c50
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594211"
---
# <a name="visual-c-intellisense-features"></a>Funkce C++ Visual IntelliSense

IntelliSense je název, který je dán pro sadu funkcí, které usnadňují kódování. Technologie IntelliSense C++ pro je k dispozici pro samostatné soubory a také pro soubory, které jsou součástí C++ projektu. V projektech pro různé platformy jsou některé funkce IntelliSense k dispozici v souborech *. cpp* a *. c* v projektu se sdíleným kódem, a to i v případě, že jste v kontextu Android nebo iOS.

Tento článek obsahuje přehled funkcí C++ technologie IntelliSense. Informace o tom, jak nakonfigurovat projekt pro technologii IntelliSense a jak řešit problémy, najdete v tématu [konfigurace C++ projektu pro technologii IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>Funkce IntelliSense vC++

IntelliSense je název, který je dán pro sadu funkcí, které usnadňují kódování. Vzhledem k tomu, že různí lidé mají různé nápady na to, co je vhodné, prakticky všechny funkce technologie IntelliSense lze povolit nebo zakázat v dialogovém okně **Možnosti** v části **textový editor** > **C++ C/**  > **Upřesnit**. Dialogové okno **Možnosti** je k dispozici v nabídce **nástroje** na panelu nabídek.

![Dialogové okno Možnosti nástroje](../ide/media/sintellisensecpptoolsoptions.PNG)

K přístupu k IntelliSense můžete použít položky nabídky a klávesové zkratky uvedené na následujícím obrázku.

![Nabídka technologie IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Dokončování příkazů a seznam členů

Při psaní klíčového slova, typu, funkce, názvu proměnné nebo jiného prvku programu, který kompilátor rozpozná, Editor nabízí příkaz pro dokončení slova.

Seznam ikon a jejich význam naleznete v tématu [zobrazení tříd a prohlížeč objektů ikony](../ide/class-view-and-object-browser-icons.md).

![Okno dokončení&#43; &#43; Wordu v jazyce Visual c++](../ide/media/vs2015_cpp_complete_word.png)

Při prvním vyvolání seznamu členů se zobrazí pouze členové, kteří jsou k dispozici pro aktuální kontext. Po stisknutí klávesy **Ctrl**+**J** se zobrazí všichni členové bez ohledu na přístupnost. Pokud ji vyvoláte třetí, zobrazí se ještě širší seznam prvků programu. Seznam členů můžete vypnout v dialogovém okně **Možnosti** v části **textový editor** > **C++ C/**  > **Obecné** > **Automatické seznamy členů**.

![Seznam členů&#43; &#43; Visual C](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Help – parametr

Když zadáte levou složenou závorku volání funkce nebo lomené závorky v deklaraci proměnné šablony třídy, editor zobrazí malé okno s typy parametrů pro každé přetížení funkce nebo konstruktoru. Parametr Current&mdash;založený na umístění kurzoru&mdash;je tučným písmem. Informace o parametrech můžete vypnout v dialogovém okně **Možnosti** v části **textový editor** > **C/C++**  > **Obecné** **informace o parametrech** > .

![Visual c++&#43; &#43; – Help – parametr](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Rychlé informace

Při najetí ukazatele myši na proměnnou se zobrazí malé okno s vložením, které zobrazuje informace o typu a záhlaví, ve kterém je typ definován. Pokud chcete zobrazit signaturu funkce, najeďte myší na volání funkce. Rychlé informace můžete vypnout v dialogovém okně **Možnosti** v části **textový editor** > **C++ C/**  > **Upřesnit** > **automatické rychlé informace**.

![Visual C&#43; &#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Chyba vlnovek

Vlnovky pod prvkem programu (proměnná, klíčové slovo, složené závorky, název typu atd.) volají upozornění na chybu nebo potenciální chybu v kódu. Při psaní dopředné deklarace se zobrazí zelená vlnovka, aby bylo možné připomenout, že je stále potřeba napsat implementaci. Fialová vlnovka se zobrazí ve sdíleném projektu, pokud dojde k chybě v kódu, který není aktuálně aktivní, například při práci v kontextu systému Windows, ale zadejte něco, co by bylo v kontextu Androidu chyba. Červená vlnovka značí chybu kompilátoru nebo upozornění v aktivním kódu, který je třeba zabývat.

![Vlnová&#43; &#43; Chyba jazyka Visual C](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Zabarvení kódu a písma

Výchozí barvy a písma lze změnit v dialogovém okně **Možnosti** v části **prostředí** > **písma a barvy**. Můžete změnit písma pro mnoho oken uživatelského rozhraní, nikoli jenom Editor. Nastavení, která jsou specifická pro C++ začátek s "C++"; Ostatní nastavení platí pro všechny jazyky.

## <a name="cross-platform-intellisense"></a>IntelliSense pro různé platformy

V projektu se sdíleným kódem jsou k dispozici některé funkce IntelliSense, jako jsou například vlnovky, i když pracujete v kontextu Androidu. Pokud napíšete kód, který by způsobil chybu v neaktivním projektu, IntelliSense stále zobrazuje vlnovky, ale mají jinou barvu než vlnovky pro chyby v aktuálním kontextu.

Vezměte v úvahu aplikaci OpenGL, která je nakonfigurovaná pro vytváření pro Android a iOS. Na ilustraci se zobrazuje upravovaný sdílený kód. V tomto obrázku je aktivní projekt **iOS. StaticLibrary**:

![pro iOS je vybraný jako aktivní projekt.](../ide/media/intellisensecppcrossplatform2.png)

Všimněte si následujícího:

- Větev `#ifdef` na řádku 6 je šedá, aby označovala neaktivní oblast, protože pro projekt iOS není definováno `__ANDROID__`.

- Proměnná pozdravu na řádku 11 je inicializována s identifikátorem `HELLO`, který nyní obsahuje červenou vlnovku. Důvodem je to, že v aktuálně aktivním projektu iOS není definován žádný identifikátor `HELLO`.

- Řádek 12 má na identifikátoru fialovou vlnovkou `BYE`, protože tento identifikátor není definovaný v (aktuálně) neaktivním projektu **Android. NativeActivity** . I když je tento řádek zkompilován, když je iOS aktivním projektem, nebude zkompilován, pokud je Android aktivním projektem. Vzhledem k tomu, že se jedná o sdílený kód, je nutné kód opravit, i když se zkompiluje v aktuálně aktivní konfiguraci.

Změníte-li aktivní projekt na Android, změní se vlnovky:

- Větev `#else` na řádku 8 je zobrazena šedě, aby označovala neaktivní oblast, protože `__ANDROID__` je definována pro projekt pro Android.

- Proměnná pozdravu na řádku 11 je inicializována s identifikátorem `HELLO`, který má fialovou vlnovkou. Důvodem je to, že v aktuálně neaktivním projektu iOS není definovaný žádný identifikátor `HELLO`.

- Řádek 12 obsahuje červenou vlnovku na identifikátoru `BYE`, protože tento identifikátor není definován v aktivním projektu.

## <a name="intellisense-for-stand-alone-files"></a>IntelliSense pro samostatné soubory

Když otevřete jeden soubor mimo libovolný projekt, budete mít i nadále IntelliSense. Můžete povolit nebo zakázat konkrétní funkce technologie IntelliSense v dialogovém okně **Možnosti** v části **textový editor** > **C/C++**  > **Upřesnit**. Pro konfiguraci technologie IntelliSense pro samostatné soubory, které nejsou součástí projektu, vyhledejte část **IntelliSense a procházení pro neprojektové soubory** .

![IntelliSense s&#43; &#43; jedním souborem v jazyce Visual c++](../ide/media/vs2015_cpp_single_file_intellisense.png)

Ve výchozím nastavení používá technologie IntelliSense pro hledání hlavičkových souborů jenom standardní adresáře include. Chcete-li přidat další adresáře, otevřete místní nabídku v uzlu **řešení** a přidejte svůj adresář do seznamu **zdrojového kódu ladění** , jak ukazuje následující obrázek:

![Přidání cesty k souboru hlaviček.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Povolit nebo zakázat funkce

Vzhledem k tomu, že různí lidé mají různé nápady na to, co je vhodné, prakticky všechny funkce technologie IntelliSense lze povolit nebo zakázat v dialogovém okně **Možnosti** v části **textový editor** > **C++ C/**  > **Upřesnit**. Dialogové okno **Možnosti** je k dispozici v nabídce **nástroje** na panelu nabídek.

![Dialogové okno Možnosti nástroje](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Viz také:

- [Používání atributu IntelliSense](../ide/using-intellisense.md)
- [Konfigurace C++ projektu pro technologii IntelliSense](visual-cpp-intellisense-configuration.md)
