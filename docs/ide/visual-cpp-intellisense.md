---
title: C++ IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: c0d1be12f733a858bf223fb1dce6a091c0dc6c50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594211"
---
# <a name="visual-c-intellisense-features"></a>Funkce Visual C++ IntelliSense

IntelliSense je název pro sadu funkcí, které usnadňují kódování. Technologie IntelliSense for C++ je k dispozici pro samostatné soubory i pro soubory, které jsou součástí projektu jazyka C++. V projektech napříč platformami jsou některé funkce Technologie IntelliSense k dispozici v souborech *CPP* a *.c* v projektu sdíleného kódu, i když jste v kontextu Androidnebo iOS.

Tento článek obsahuje přehled funkcí Jazyka C++ IntelliSense. Informace o konfiguraci projektu pro technologie IntelliSense a řešení problémů naleznete v [tématu Konfigurace projektu jazyka C++ pro technologie IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>Funkce Technologie IntelliSense v jazyce C++

IntelliSense je název pro sadu funkcí, které usnadňují kódování. Vzhledem k tomu, že různí lidé mají různé představy o tom, co je výhodné, prakticky všechny funkce Technologie IntelliSense mohou být povoleny nebo zakázány v dialogovém okně **Možnosti** v části **Textový editor** > **C/C++** > **Upřesnit**. Dialogové okno **Volby** je k dispozici v nabídce **Nástroje** na řádku nabídek.

![Dialogové okno Volby nástroje](../ide/media/sintellisensecpptoolsoptions.PNG)

Pro přístup k programu IntelliSense můžete použít položky nabídky a klávesové zkratky zobrazené na následujícím obrázku.

![Nabídka IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Dokončení výkazu a seznam členů

Když začnete psát klíčové slovo, typ, funkci, název proměnné nebo jiný prvek programu, který kompilátor rozpozná, editor nabídne k dokončení slova pro vás.

Seznam ikon a jejich významu naleznete v [tématu Ikony zobrazení tříd a Prohlížeče objektů](../ide/class-view-and-object-browser-icons.md).

![Okno Visual C&#43;&#43; Complete Word](../ide/media/vs2015_cpp_complete_word.png)

Při prvním vyvolání seznamu členů zobrazí pouze členy, které jsou přístupné pro aktuální kontext. Pokud poté stisknete **kombinaci kláves Ctrl**+**J,** zobrazí se všechny členy bez ohledu na přístupnost. Pokud jej vyvoláte potřetí, zobrazí se ještě širší seznam prvků programu. Seznam členů můžete vypnout v dialogovém okně **Možnosti** v části **Text Editor** > **C/C++** > **Členové seznamu****General** > Auto .

![Seznam členů Visual C&#43;&#43; ](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Nápověda k parametrům

Když zadáte otevírací složenku volání funkce nebo úhlové závorky na deklaraci proměnné šablony třídy, editor zobrazí malé okno s typy parametrů pro každé přetížení funkce nebo konstruktoru. Parametr "aktuální"&mdash;založený na&mdash;umístění kurzoru je tučně. Informace o parametrech můžete vypnout v dialogovém okně **Možnosti** v části **Textový editor** > **C/C++** > Informace o**obecném** > **parametru**.

![Nápověda k parametru Visual C&#43;&#43; ](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Rychlé informace

Když najedete kurzorem myši nad proměnnou, zobrazí se malé okno s informacemi o textu a záhlavím, ve kterém je typ definován. Najeďte přes volání funkce a zobcemte podpis funkce. Rychlé informace můžete vypnout v dialogovém okně **Možnosti** v části **Textový editor** > **C/C++** > **Rozšířené** > **automatické rychlé informace**.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Chyba vlnovky

Vlnovky pod elementem programu (proměnná, klíčové slovo, složená závorka, název typu a tak dále) vás upozorní na chybu nebo potenciální chybu v kódu. Zelená vlnovka se zobrazí při psaní dopředné deklarace, aby vám připomněl, že stále potřebujete napsat implementaci. Fialová vlnovka se zobrazí ve sdíleném projektu, pokud je chyba v kódu, který není aktuálně aktivní, například při práci v kontextu systému Windows, ale zadejte něco, co by byla chyba v kontextu Android. Červená vlnovka označuje chybu kompilátoru nebo upozornění v aktivním kódu, který je třeba řešit.

![Chyba Visual C&#43;&#43; se vlní](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Zbarvení kódu a písma

Výchozí barvy a písma lze změnit v dialogovém okně **Volby** v části**Písma a barvy** **prostředí** > . Můžete změnit písma pro mnoho oken ui zde, nejen editor. Nastavení, která jsou specifická pro C++ začínají "C++"; ostatní nastavení jsou pro všechny jazyky.

## <a name="cross-platform-intellisense"></a>Technologie IntelliSense napříč platformami

V projektu sdíleného kódu jsou některé funkce Technologie IntelliSense, jako jsou vlnovky, k dispozici, i když pracujete v kontextu systému Android. Pokud napíšete nějaký kód, který by vedl k chybě v neaktivním projektu, technologie IntelliSense stále zobrazuje vlnovky, ale jsou v jiné barvě než klikyháky pro chyby v aktuálním kontextu.

Zvažte aplikaci OpenGLES, která je nakonfigurovaná pro android a iOS. Obrázek znázorňuje upravovaný sdílený kód. V tomto obrázku je aktivní projekt **iOS.StaticLibrary**:

![jako aktivní projekt je vybrán iOS.](../ide/media/intellisensecppcrossplatform2.png)

Všimněte si následujícího:

- Větev `#ifdef` na řádku 6 je šedě zobrazena, aby označovala neaktivní oblast, protože `__ANDROID__` není definována pro projekt iOS.

- Proměnná pozdravu na řádku 11 `HELLO`je inicializována s identifikátorem , který má nyní červenou vlnovku. Důvodem je, `HELLO` že žádný identifikátor je definován v aktuálně aktivní ms projektu iOS.

- Řádek 12 má fialovou vlnovku na identifikátor, `BYE` protože tento identifikátor není definován v (aktuálně) neaktivní **Android.NativeActivity** projektu. I když tento řádek zkompiluje, když iOS je aktivní projekt, nebude kompilovat, když Android je aktivní projekt. Vzhledem k tomu, že se jedná o sdílený kód, měli byste jej opravit, i když se zkompiluje v aktuálně aktivní konfiguraci.

Pokud změníte aktivní projekt na Android, změní se vlnovky:

- Větev `#else` na řádku 8 je šedě zobrazena, aby označovala neaktivní oblast, protože `__ANDROID__` je definována pro projekt Android.

- Proměnná pozdravu na řádku 11 `HELLO`je inicializována s identifikátorem , který má fialovou vlnovku. Důvodem je, `HELLO` že žádný identifikátor je definován v aktuálně neaktivní iOS projektu.

- Řádek 12 má červenou vlnovku na identifikátor, `BYE` protože tento identifikátor není definován v aktivním projektu.

## <a name="intellisense-for-stand-alone-files"></a>Technologie IntelliSense pro samostatné soubory

Když otevřete jeden soubor mimo libovolný projekt, stále získáte IntelliSense. V dialogovém okně **Možnosti** v části **Textový editor** > **C/C++** > **Upřesnit**můžete povolit nebo zakázat určité funkce Technologie IntelliSense. Chcete-li nakonfigurovat službu IntelliSense pro jednotlivé soubory, které nejsou součástí projektu, vyhledejte v části **IntelliSense a procházení neprojektových souborů.**

![Visual C&#43;&#43; jeden soubor intellisense](../ide/media/vs2015_cpp_single_file_intellisense.png)

Ve výchozím nastavení používá technologie IntelliSense pouze standardní adresáře pro zahrnutí k vyhledání souborů hlaviček. Chcete-li přidat další adresáře, otevřete místní nabídku v uzlu **Řešení** a přidejte adresář do seznamu **Ladění zdrojového kódu,** jak ukazuje následující obrázek:

![Přidání cesty k souboru záhlaví.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Povolení nebo zakázání funkcí

Vzhledem k tomu, že různí lidé mají různé představy o tom, co je výhodné, prakticky všechny funkce Technologie IntelliSense mohou být povoleny nebo zakázány v dialogovém okně **Možnosti** v části **Textový editor** > **C/C++** > **Upřesnit**. Dialogové okno **Volby** je k dispozici v nabídce **Nástroje** na řádku nabídek.

![Dialogové okno Volby nástroje](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Viz také

- [Používání atributu IntelliSense](../ide/using-intellisense.md)
- [Konfigurace projektu C++ pro IntelliSense](visual-cpp-intellisense-configuration.md)
