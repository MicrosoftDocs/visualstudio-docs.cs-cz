---
title: IntelliSense pro C++
ms.date: 10/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ab520f7cdf512ebbfd07770d63d2ed50caee7a55
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879847"
---
# <a name="visual-c-intellisense-features"></a>Funkce Visual C++ IntelliSense

Technologie IntelliSense je název zadaný pro sadu funkcí, které usnadňují psaní kódu pohodlnější. Technologie IntelliSense jazyka C++ je k dispozici pro samostatné soubory stejně jako u souborů, které jsou součástí projektu jazyka C++. V projektech pro různé platformy, některé funkce technologie IntelliSense jsou k dispozici v *.cpp* a *.c* soubory v projektu sdíleného kódu, i když jsou v kontextu Android nebo iOS.

Tento článek obsahuje přehled technologie IntelliSense jazyka C++, funkce. Informace o tom, jak nakonfigurovat projekt tak, aby IntelliSense a řešení potíží, najdete v části [konfigurace projektu C++ IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>Funkce technologie IntelliSense v jazyce C++

Technologie IntelliSense je název zadaný pro sadu funkcí, které usnadňují psaní kódu pohodlnější. Protože různé myšlenky o tom, co je vhodné mají různí lidé, téměř všechny funkce technologie IntelliSense můžete povolit nebo zakázat v **možnosti** dialogovém okně **textový Editor**  >  **C/C++** > **Advanced**. **Možnosti** dialogové okno je k dispozici **nástroje** nabídky na řádku nabídek.

![Nástroj pro dialogové okno Možnosti](../ide/media/sintellisensecpptoolsoptions.PNG)

Pro přístup k IntelliSense můžete použít položky nabídky a klávesové zkratky je znázorněno na následujícím obrázku.

![Nabídky technologie IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Příkaz dokončení a člena seznamu

Když začnete psát klíčové slovo, typ, funkce, název proměnné nebo jiný prvek programu, který kompilátor rozpozná, editor nabízí dokončit slovo za vás.

Seznam ikon a jejich vysvětlení najdete v tématu [ikony zobrazení třídy a prohlížeče objektů](../ide/class-view-and-object-browser-icons.md).

![Visual C&#43; &#43; okno Dokončit slovo](../ide/media/vs2015_cpp_complete_word.png)

Při prvním vyvolání seznamu členů, pouze zobrazuje členy, které jsou k dispozici pro aktuální kontext. Pokud stisknete **Ctrl**+**J** , zobrazuje všechny členy, bez ohledu na přístupnost. Pokud jste ho vyvolat třetí čas, zobrazí se ještě širší seznam prvky programu. Můžete ji vypnout seznam členů v **možnosti** dialogovém okně **textový Editor** > **C/C++** > **Obecné**  >  **Automatický seznam členů**.

![Visual C&#43; &#43; seznam členů](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Parametr nápovědy

Když zadáte levá složená závorka volání funkce nebo ostré závorky v deklaraci proměnné šablony třídy, editor hlásí malém okně se typy parametrů pro jednotlivá přetížení funkce nebo konstruktoru. Parametr "aktuální"&mdash;podle umístění kurzoru&mdash;je zvýrazněný tučným písmem. Můžete ji vypnout informace o parametrech v **možnosti** dialogovém okně **textový Editor** > **C/C++** > **Obecné**  >  **Informace o parametrech**.

![Visual C&#43; &#43; nápovědu](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Rychlé informace

Když najedete myší do přes proměnnou, se zobrazí v textu, který zobrazuje informace o typu a záhlaví, ve kterém je typ definován malém okně. Najeďte myší volání funkce pro zjištění signatury funkce. Můžete ji vypnout rychlé informace v **možnosti** dialogovém okně **textový Editor** > **C/C++** > **Upřesnit**  >  **Automatické rychlé informace**.

![Visual C&#43; &#43; rychlé informace](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Podtržení vlnovkou u chyb

Podtržení vlnovkou pod prvek programu (proměnné, klíčové slovo, složenou závorku, název typu a tak dále) volat vaši pozornost na chybu nebo potenciální chyby v kódu. Při psaní Dopředná deklarace s připomínkou, že je stále potřeba napsat implementaci, zobrazí se zelená vlnovku. Nachová vlnovku se zobrazí ve sdíleném projektu při chybě v kódu, který není aktuálně aktivní, například při práci v rámci Windows, ale zadejte jinou hodnotu, která by byla chybu v kontextu s Androidem. Červená vlnovka označuje kompilátor chybu nebo upozornění v aktivním kódem, který je potřeba řešit.

![Visual C&#43; &#43; podtržení vlnovkou u chyb](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Zabarvení kódu a písem

Výchozí barev a písem lze změnit v **možnosti** dialogovém okně **prostředí** > **písma a barvy**. Můžete změnit písma pro mnoho uživatelského rozhraní systému windows, nejen editoru. Nastavení, které se týkají C++ začínají řetězcem "C++"; ostatní nastavení se pro všechny jazyky.

## <a name="cross-platform-intellisense"></a>Multiplatformní IntelliSense

V projektu sdíleného kódu jsou k dispozici některé funkce technologie IntelliSense, jako je například podtržení vlnovkou, i v případě, že pracujete v Androidu kontextu. Pokud píšete kód, který by dojít k chybě v projektu aplikace neaktivní, technologie IntelliSense zobrazuje podtržení vlnovkou, ale jsou jinou barvou, než podtržení vlnovkou u chyb v rámci aktuálního kontextu.

Vezměte v úvahu aplikace OpenGLES, který je nakonfigurován pro sestavení pro Android a iOS. Na obrázku ukazuje sdílený kód, který právě upravujete. Na tomto obrázku je aktivní projekt **iOS.StaticLibrary**:

![iOS je vybrán jako aktivní projekt.](../ide/media/intellisensecppcrossplatform2.png)

Všimněte si následujícího:

- `#ifdef` Větve na řádku 6 je zobrazena šedě označuje aktivní oblast, protože `__ANDROID__` není definovaný pro projekt pro iOS.

- Pozdrav proměnná na řádku 11 je inicializována s identifikátorem `HELLO`, které je teď má červená vlnovka. Důvodem je, že žádný identifikátor `HELLO` je definován v projektu pro iOS aktuálně aktivní.

- Řádek 12 má nachová vlnovku na identifikátor `BYE` vzhledem k tomu, že tento identifikátor není definován v (aktuálně) neaktivní **Android.NativeActivity** projektu. Přestože tento řádek zkompiluje, pokud je aktivní projekt iOS, nebude zkompilován při Android je aktivní projekt. Protože se sdíleným kódem, měli byste opravit kód i v případě, že se zkompiluje v současné době aktivní konfiguraci.

Pokud změníte aktivní projekt pro Android, změňte podtržení vlnovkou:

- `#else` Větve na řádku 8 je zobrazena šedě označuje aktivní oblast, protože `__ANDROID__` definovaný pro projekt pro Android.

- Pozdrav proměnná na řádku 11 je inicializována s identifikátorem `HELLO`, který má nachová vlnovku. Důvodem je, že žádný identifikátor `HELLO` je definován v projektu pro iOS aktuálně neaktivní.

- Řádek 12 má červená vlnovka na identifikátor `BYE` vzhledem k tomu, že tento identifikátor není definován aktivního projektu.

## <a name="intellisense-for-stand-alone-files"></a>Technologie IntelliSense pro samostatné soubory

Při otevření jednoho souboru mimo jakýkoli projekt stále získání funkce IntelliSense. Můžete povolit nebo zakázat konkrétní funkce technologie IntelliSense v **možnosti** dialogovém okně **textový Editor** > **C/C++**  >  **Advanced**. Chcete-li nakonfigurovat technologie IntelliSense pro jednotlivé soubory, které nejsou součástí projektu, vyhledejte **technologie IntelliSense a procházení pro neprojektové soubory** oddílu.

![Visual C&#43; &#43; jednoho souboru intellisense](../ide/media/vs2015_cpp_single_file_intellisense.png)

Ve výchozím nastavení, jednosouborová IntelliSense využívá pouze standardní adresáře souborů k zahrnutí k vyhledání souborů záhlaví. Chcete-li přidat další adresáře, otevřete místní nabídku na **řešení** uzlu a přidejte do adresáře **ladění zdrojový kód** seznam, jak je vidět na následujícím obrázku:

![Přidání cesty k souboru hlaviček.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Povolení nebo zakázání funkcí

Protože různé myšlenky o tom, co je vhodné mají různí lidé, téměř všechny funkce technologie IntelliSense můžete povolit nebo zakázat v **možnosti** dialogovém okně **textový Editor**  >  **C/C++** > **Advanced**. **Možnosti** dialogové okno je k dispozici **nástroje** nabídky na řádku nabídek.

![Nástroj pro dialogové okno Možnosti](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Viz také:

- [Používání atributu IntelliSense](../ide/using-intellisense.md)
- [Konfigurace projektu C++ IntelliSense](visual-cpp-intellisense-configuration.md)
