---
title: Visual C++ Intellisense | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ced999c20678cc64dc5f96e86070b5f39d5ca2c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881674"
---
# <a name="visual-c-intellisense"></a>Visual C++ IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio 2015 je k dispozici pro jeden kód soubory stejně jako soubory v projektech technologie IntelliSense. V projektech pro různé platformy některé funkce technologie IntelliSense jsou k dispozici v souborech .cpp a .c v projektu sdíleného kódu i v případě, že jsou v kontextu Android nebo iOS.  
  
## <a name="intellisense-features-in-c"></a>Funkce technologie IntelliSense v jazyce C++  
 Technologie IntelliSense je název zadaný pro sadu funkcí, které usnadňují psaní kódu pohodlnější. Protože různé myšlenky o tom, co je vhodné mají různí lidé, téměř všechny funkce technologie IntelliSense můžete povolit nebo zakázat v **textový Editor, C/C++, Upřesnit** stránku vlastností.  
  
 ![Nástroje, možnosti, textový Editor, C&#47;C&#43;&#43;, pokročilé](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")  
  
 Pro přístup k IntelliSense můžete použít položky nabídky a klávesové zkratky je znázorněno na následujícím obrázku.  
  
 ![Visual C&#43; &#43; nabídky technologie IntelliSense](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")  
  
### <a name="statement-completion-and-member-list"></a>Příkaz dokončení a člena seznamu  
 Když začnete psát klíčové slovo, typ, funkce, název proměnné nebo jiný prvek programu, který kompilátor rozpozná, editor nabízí dokončit slovo můžete  
  
 Seznam ikon a jejich vysvětlení najdete v tématu [třídy View and Object Browser Icons](../ide/class-view-and-object-browser-icons.md).  
  
 ![Visual C&#43; &#43; okno Dokončit slovo](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")  
  
 Při prvním vyvolání seznam členů pouze zobrazuje členy, které jsou k dispozici pro aktuální kontext. Pokud používáte **Ctrl + J** , zobrazuje všechny členy, bez ohledu na přístupnost. Pokud jste ho vyvolat třetí čas, zobrazí se ještě širší seznam prvky programu. Můžete ji vypnout dokončování příkazů ve **možnosti jazyka C/C++ General** stránky.  
  
 ![Visual C&#43;&#43; Member List](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")  
  
### <a name="parameter-help"></a>Parametr nápovědy  
 Když zadáte levá složená závorka volání funkce nebo ostré závorky v deklaraci proměnné šablony třídy, editor hlásí malém okně se typy parametrů pro jednotlivá přetížení funkce nebo konstruktoru. Parametr "aktuální" – v závislosti na umístění kurzoru – je zvýrazněný tučným písmem. Můžete ji vypnout dokončování příkazů ve **možnosti jazyka C/C++ General** stránky.  
  
 ![Visual C&#43;&#43; Parameter Help](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")  
  
### <a name="quick-info"></a>Rychlé informace  
 Když najedete myší do přes proměnnou, se zobrazí v textu, který zobrazuje informace o typu a záhlaví, ve kterém je typ definován malém okně. Najeďte myší volání funkce pro zjištění signatury funkce. Můžete ji vypnout rychlé informace v **textový Editor, C/C++, Upřesnit** stránky.  
  
 ![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")  
  
## <a name="error-squiggles"></a>Podtržení vlnovkou u chyb  
 Podtržení vlnovkou pod prvek programu (proměnné, klíčové slovo, složenou závorku, název typu a tak dále) volat vaši pozornost na chybu nebo potenciální chyby v kódu. Při psaní Dopředná deklarace s připomínkou, že je stále potřeba napsat implementaci, zobrazí se zelená vlnovku. Nachová vlnovku se zobrazí ve sdíleném projektu při chybě v kódu, který není aktuálně aktivní, například při práci v rámci Windows, ale zadejte jinou hodnotu, která by byla chybu v kontextu s Androidem. Červená vlnovka označuje kompilátor chybu nebo upozornění v aktivním kódem, který je potřeba řešit.  
  
 ![Visual C&#43; &#43; podtržení vlnovkou u chyb](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")  
  
## <a name="code-colorization-and-fonts"></a>Zabarvení kódu a písem  
 Výchozí barev a písem lze změnit pomocí **prostředí, písma a barvy** stránku vlastností. Můžete změnit písma pro mnoho uživatelského rozhraní systému windows, nejen editoru. Nastavení, které se týkají C++ začínají řetězcem "C++"; ostatní nastavení se pro všechny jazyky.  
  
## <a name="cross-platform-intellisense"></a>Multiplatformní IntelliSense  
 V projektu sdíleného kódu jsou k dispozici některé funkce technologie IntelliSense, jako je například podtržení vlnovkou, i v případě, že pracujete v Androidu kontextu. Pokud píšete kód, který by dojít k chybě v projektu aplikace neaktivní, technologie IntelliSense zobrazuje podtržení vlnovkou, ale jsou jinou barvou, než podtržení vlnovkou u chyb v rámci aktuálního kontextu.  
  
 Tady je aplikace OpenGLES, který je nakonfigurován pro sestavení pro Android a iOS. Na obrázku ukazuje sdílený kód, který právě upravujete. Na prvním obrázku Android je aktivní projekt:  
  
 ![Projekt pro Android je aktivní projekt. ](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")  
  
 Všimněte si následujícího:  
  
- #Else větve na řádku 8 je zobrazena šedě označuje aktivní oblast, protože `__ANDROID__` definovaný pro projekt pro Android.  
  
- Pozdrav proměnná na řádku 11 je inicializována s identifikátorem HELLO, který má nachová vlnovku. Je to proto, že žádný identifikátor HELLO je definován v projektu pro iOS aktuálně neaktivní. Když v Androidu by zkompilovat projekt řádku 11, nebudou v iOS. Protože se jedná o sdílený kód, který je něco, měli byste změnit i v případě, že se zkompiluje v současné době aktivní konfiguraci.  
  
- Řádek 12 má červená vlnovka na identifikátor BYE; Tento identifikátor není definován v aktuálně vybraného aktivního projektu.  
  
  Nyní změnit aktivní projekt iOS.StaticLibrary a Všimněte si, jak se mění podtržení vlnovkou.  
  
  ![iOS je vybrán jako aktivní projekt. ](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")  
  
  Všimněte si následujícího:  
  
- #Ifdef větve na řádku 6 je zobrazena šedě označuje aktivní oblast, protože *_ANDROID\\*  \_ není definovaný pro projekt pro iOS.  
  
- Pozdrav proměnná na řádku 11 je inicializována s identifikátorem HELLO, který má teď červená vlnovka. Je to proto, že žádný identifikátor HELLO je definován v projektu pro iOS aktuálně aktivní.  
  
- Řádek 12 má nachová vlnovku na identifikátor BYE; Tento identifikátor není definován v aktuálně neaktivní Android.NativeActivity projektu.  
  
## <a name="single-file-intellisense"></a>Jeden soubor IntelliSense  
 Při otevření jednoho souboru mimo jakýkoli projekt stále získání funkce IntelliSense. Můžete povolit nebo zakázat konkrétní funkce tak, že přejdete do **textový Editor, C/C++, Upřesnit** můžete zapnout nebo vypnout funkce technologie IntelliSense. Chcete-li nakonfigurovat technologie IntelliSense pro jednotlivé soubory, které nejsou součástí projektu, vyhledejte **technologie IntelliSense a procházení pro neprojektové soubory** v **Upřesnit** oddílu. Zobrazit [průvodce Visual C++](http://msdn.microsoft.com/en-us/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).  
  
 ![Visual C&#43; &#43; jednoho souboru intellisense](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")  
  
 Ve výchozím nastavení, jednosouborová IntelliSense využívá pouze standardní adresáře souborů k zahrnutí k vyhledání souborů záhlaví. Chcete-li přidat další adresáře, otevřete místní nabídku uzlu řešení a přidejte do adresáře **ladění zdrojový kód** seznam, jak je vidět na následujícím obrázku:  
  
 ![Přidání cesty k souboru hlaviček. ](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu IntelliSense](../ide/using-intellisense.md)



