---
title: Import projektu XCode | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b0e42c167e87f19781f9544e20e7870789af4ef9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754156"
---
# <a name="import-an-xcode-project"></a>Import projektu XCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Microsoft Visual C++ pro vývoj mobilních řešení napříč platformami zahrnuje podporu pro přesun projektů XCode do sady Visual Studio, kde můžete vytvářet multiplatformní knihovny a sdílení kódu pomocí jiných projektů. Importovat z Xcodu Průvodce zjednodušuje proces importu projektů a rozdělení kódu C++ v XCode cílů pro použití jako statická knihovna nebo sdíleného projektu kódu. Můžete spravovat váš kód specifický pro iOS v sadě Visual Studio a dál používat XCode pro scénáře a sestavení. Informace o tom, jak snadno přesunout vpřed a zpět mezi sadou Visual Studio a XCode kódu najdete v tématu přesunout změn mezi XCode a sadou Visual Studio.  
  
## <a name="using-the-import-from-xcode-wizard"></a>Pomocí Průvodce importovat z Xcodu  
 Toto téma ukazuje, jak přesunout projekt XCode do sady Visual Studio, abyste mohli využívat sdílení kódu a řešení pro různé platformy. Předpokladem je musí spárovat počítači Mac k sadě Visual Studio, abyste mohli k importu, exportu a sestavte projekt. Pokyny o tom, jak nastavit párování najdete v tématu [instalace a konfigurace nástrojů pro vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Musíte také sdílet váš projekt XCode v síti nebo přesunout do sady Visual Studio počítač pomocí XCode Průvodce importem.  
  
#### <a name="import-from-xcode"></a>Importovat z Xcodu  
  
1. Na **souboru** nabídce zvolte **nový**, **Import**, **importovat z Xcodu**. Tím se spustí **importovat z Xcodu** dialogové okno průvodce.  
  
    ![Zvolte cílový projekt XCode pro import](../cross-platform/media/cppmdd-u2-importxcode-choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. V **zvolit projekt** podokně klikněte na tlačítko Procházet a vyberte soubor .pbxproj XCode. Přejděte k souboru projektu v **soubor projektu XCode vyberte** dialogového okna a klikněte na tlačítko **otevřít**.  
  
    ![Vyberte soubor projektu v dialogovém okně vyberte Xcode projektu soubor](../cross-platform/media/cppmdd-u2-importxcode-browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    V XCode Průvodce importem, zvolte **Další**.  
  
3. V **cíle** podokně zvolte cíle z projektu XCode pro import do projektů sady Visual Studio. XCode cíle jsou podobné projektů sady Visual Studio; Většina je kolekce kód a prostředky, které vytvoří binární soubor. Importovat z Xcodu Průvodce může import cílů, které vytvoří binární soubor, ale ne statickou knihovnu, jako cíle. XCode statickou knihovnu cíle jsou předmětem na další krok.  
  
    ![Importovat z Xcodu Průvodce cíle podokna](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    Pro každý cíl vybraný v **cíle pro import**, průvodce automaticky zjistí soubory kódu C++, které je možné rozdělit na samostatné statické knihovny projektu a umístí je **položky projektu C++** oddílu. Další kód a prostředky jsou ponechána v **položky projektu XCode** oddílu. Tyto stane samostatnou statickou knihovnu a projekty aplikací v sadě Visual Studio po dokončení procesu importu. Jednotka testu a rozhraní framework cíle nejsou ve výchozím nastavení, rozdělte na samostatné projekty pomocí průvodce.  
  
    Chcete-li změnit, které soubory jsou v každém projektu, použijte nahoru a dolů. Pokud jste spokojeni s soubory v každém projektu, zvolte **Další** pokračujte.  
  
4. V **cíle představující knihovny** podokně zvolte, které statickou knihovnu, zaměřuje z projektu XCode pro import do projektů sady Visual Studio. V tomto podokně můžete soubory, které jsou umístěny v projektu sdíleného kódu, a které jsou umístěny v projektu statické knihovny. V každém cíli v **cíle pro import** seznamu, můžete určit, které soubory jsou umístěny v **položky projektu sdíleného kódu** a **položky projektu statické knihovny** pomocí nahoru a dolů.  
  
    ![Import z podokna cíle představující knihovny XCode](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    Sdílený kód projektu je způsob sdílení sadu souborů zdrojového kódu mezi projekty v sadě Visual Studio. Kód je sestavený jako součást projektu, který ji obsahuje, nikoli jako v projektu. Protože projekty, které zahrnují sdílený kód může mít různé architektury a konfigurace, toto je nejlepší způsob, jak poskytnout jednoho projektu, který obsahuje kód, který může být sestaveny pro různé platformy.  
  
    Pokud jste spokojeni s soubory v každém projektu, zvolte **Další** pokračujte.  
  
5. **Globální vlastnosti** podokně je možné nastavit cestu pro vyhledání rozhraní a cestu k zahrnout záhlaví vyhledávání pro všechny projekty iOS v sadě Visual Studio. Visual Studio používá tyto cesty k procházení zdrojového kódu a technologie IntelliSense. Tyto globální cesty jsou užitečné, když vytváříte projekty iOS využívající společnou sadu záhlaví a architektur.  
  
    ![Import z podokna XCode globální vlastnosti](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    Tyto globální cesty lze také nastavit v sadě Visual Studio **možnosti** dialogového okna. Je, vyhledejte na **nástroje** nabídce vyberte možnost **možnosti**. V **možnosti** dialogového okna, rozbalte **různé platformy**, **C++**, **iOS**, **globální vlastnosti**.  
  
    Zvolte **Další** pokračujte.  
  
6. **Architektury** podokno se používá ke konfiguraci cesty používá sada Visual Studio pro procházení a IntelliSense pro váš projekt. Cesty musí být přístupná pro Visual Studio pro každé rozhraní, které odkazuje váš projekt XCode. Průvodce ověří rozhraní odkazuje v projekty XCode a zobrazuje, zda sada Visual Studio můžete najít rozhraní framework. Jakoukoli cestu, kterou jste už nastavili v globální vlastnosti by měly být zjištěny pomocí sady Visual Studio. Výjimky jsou uvedeny v seznamu rozhraní. Pro každé rozhraní, které jsou uvedeny x zadejte cestu počítače přístupné pro Visual Studio najít rozhraní framework. Tlačítko pro procházení [...] můžete použít **vybrat složku** dialogového okna najít cestu. Cesta framework může být buď místní kopii nebo síťově přístupné sdílené složky na vašem počítači Mac.  
  
    ![Import z podokna rozhraní XCode](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    Zvolte **Další** pokračujte.  
  
7. **Nastavení projektu** podokně umožňuje změnit rozhraní framework a zahrnout záhlaví nastavení cesty hledání pro každý projekt vytvoří. V tomto podokně můžete nastavit cesty specifické pro projekt, které se liší od globálního nastavení.  
  
    V nastavení cesty ke konkrétnímu projektu **cílový projekt** rozevíracího seznamu, vyberte soubor projektu a pak nastavte hodnoty **cesta pro vyhledání rozhraní** a **zahrnout cestu pro vyhledání hlaviček** ovládacích prvků. Tlačítko pro procházení [...] vedle každého ovládacího prvku můžete použít **vybrat složku** dialogového okna najít cestu.  
  
    ![Import z podokna projekty XCode](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    Pokud se tento počítač v sadě Visual Studio není spárovaný žádný vzdálený Mac, konfigurací odkazem na vzdáleném počítači uveden. Pokyny o tom, jak nastavit párování najdete v tématu [instalace a konfigurace nástrojů pro vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
    Chcete-li importovat projekt XCode v nastavení v průvodci, zvolte **importovat**.  
  
   Importovat z Xcodu Průvodce vytvoří projekty v sadě Visual Studio, která odpovídá vybrané cíle projektu XCode. Kód, který můžete sdílet s jinými projekty C++ je rozdělit na samostatné sdílenému kódu a projekty statických knihoven. Zbývající kód je umístěn v iOS projektech knihovny a aplikace, které se dají vzdáleně pomocí sady Visual Studio. Další informace o přesunutí kódu mezi sadou Visual Studio a XCode, naleznete v tématu [synchronizace změn mezi XCode a sadou Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

