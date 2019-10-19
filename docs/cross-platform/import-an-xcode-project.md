---
title: Import projektu Xcode | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 62161b612d6c4583cd2206c3d18dc6606d2d9f0b
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588897"
---
# <a name="import-an-xcode-project"></a>Import projektu Xcode

Nástroje Visual Studio Tools pro vývoj mobilních aplikací pro různé platformy C++ s podporou pro přesun projektů Xcode do sady Visual Studio, kde můžete vytvářet knihovny pro různé platformy a sdílet kód s ostatními projekty. Průvodce importem z Xcode zjednodušuje proces importu projektů a rozdělení C++ kódu do vašich cílů Xcode pro použití jako statické knihovny nebo projektu sdíleného kódu. Můžete spravovat kód specifický pro iOS v aplikaci Visual Studio a dál používat Xcode ke scénářům a sestavením. Informace o tom, jak snadno přesunout kód mezi Visual Studio a Xcode, najdete v tématu [synchronizace změn mezi Xcode a Visual Studio](sync-changes-between-xcode-and-visual-studio.md).

## <a name="use-the-import-from-xcode-wizard"></a>Použití Průvodce importem z Xcode

V tomto článku se dozvíte, jak přesunout projekt Xcode do sady Visual Studio, abyste mohli využít výhod sdílení kódu a řešení pro různé platformy. K importu, exportu a sestavování projektu musíte jako součást spárovat svůj počítač Mac s Visual Studiem. Pokyny, jak nastavit párování, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Musíte také buď sdílet svůj Xcode projekt přes síť, nebo ho přesunout do počítače s Visual Studiem, aby bylo možné použít Průvodce importem z Xcode.

### <a name="import-from-xcode"></a>Import z Xcode

1. V nabídce **soubor** klikněte na příkaz **Nový**, **importovat**a **importovat z Xcode**. Tento příkaz spustí dialogové okno průvodce **importem z Xcode** .

   ![Zvolit cílový projekt Xcode, který se má importovat](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "Zvolit cílový projekt Xcode, který se má importovat")

1. V podokně **Zvolte projekt** klikněte na tlačítko Procházet a vyberte soubor Xcode *. pbxproj* . V dialogovém okně **Vybrat soubor projektu Xcode** přejděte do souboru projektu a pak zvolte **otevřít**.

   ![Vyberte soubor projektu v dialogovém okně Vybrat soubor projektu Xcode.](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "Vyberte soubor projektu v dialogovém okně Vybrat soubor projektu Xcode.")

   V průvodci Import z Xcode klikněte na tlačítko **Další**.

1. V podokně **cílové cíle** vyberte cíle z projektu Xcode pro import do projektů sady Visual Studio. Cíle Xcode jsou podobné projektům sady Visual Studio; Většina je kolekce kódu a prostředků, které vytváří binární soubor. Průvodce importem z Xcode umožňuje pouze import cílů, které tvoří binární, ale ne statickou knihovnu, jako cílové cíle. Cíle statických knihoven Xcode jsou předmětem dalšího kroku.

   ![Podokno cílové cíle Průvodce importem z Xcode](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "Podokno cílové cíle Průvodce importem z Xcode")

   Pro každý cíl vybraný v **cíli, který se má importovat**, průvodce C++ automaticky detekuje soubory kódu, které lze rozdělit do samostatného projektu statických knihoven, a umístí je do oddílu  **C++ položky projektu** . Další kód a prostředky jsou ponechány v části **položky projektu Xcode** . Tyto projekty se stanou samostatnými statickými knihovnami a aplikacemi v aplikaci Visual Studio, jakmile průvodce dokončí proces importu. Ve výchozím nastavení se test jednotek a cíle architektury nerozdělí do samostatných projektů průvodce.

   Chcete-li změnit, které soubory jsou v každém projektu, použijte tlačítka nahoru a dolů. Až budete s soubory v každém projektu spokojeni, klikněte na tlačítko **Další** a pokračujte.

1. V podokně **cíle knihovny** vyberte statické knihovny, které jsou cíle z projektu Xcode, které chcete importovat do projektů sady Visual Studio. V tomto podokně můžete zvolit, které soubory se mají umístit do projektu sdíleného kódu a které se mají umístit do projektu statických knihoven. V každém z cílů v seznamu **cíle na Import** můžete určit, které soubory se mají umístit do **položek projektu sdíleného kódu** a **položky projektu statické knihovny** pomocí tlačítek nahoru a dolů.

   ![Podokno cílení na Import z knihovny Xcode](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "Podokno cílení na Import z knihovny Xcode")

   Projekt sdíleného kódu je způsob, jak sdílet sadu zdrojových souborů mezi projekty v sadě Visual Studio. Kód je sestaven jako součást projektu, který jej obsahuje, nikoli jako vlastní projekt. Projekty, které obsahují sdílený kód, mohou mít různé architektury a konfigurace. Projekt sdíleného kódu je nejlepším způsobem, jak poskytnout jeden projekt, který obsahuje kód, který může být sestaven pro mnoho druhů platforem.

   Až budete s soubory v každém projektu spokojeni, klikněte na tlačítko **Další** a pokračujte.

1. Pomocí podokna **globální vlastnosti** nastavte cestu pro vyhledávání rozhraní a cestu pro hledání záhlaví include pro všechny projekty iOS v sadě Visual Studio. Visual Studio používá tyto cesty pro procházení zdrojového kódu a pro IntelliSense. Tyto globální cesty jsou užitečné, když vytváříte projekty iOS, které používají společnou sadu hlaviček a architektur.

   ![Import z podokna globálních vlastností Xcode](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "Import z podokna globálních vlastností Xcode")

   Tyto globální cesty lze také nastavit v sadě Visual Studio v dialogovém okně **Možnosti** . Pokud je chcete vyhledat, v nabídce **nástroje** vyberte **Možnosti**. V dialogovém okně **Možnosti** rozbalte položku  > **C++** pro **různé platformy**  > **iOS**  > **globální vlastnosti**.

   Pokračujte kliknutím na tlačítko **Další** .

1. Podokno **architektury** se používá ke konfiguraci cest používaných v aplikaci Visual Studio pro procházení a IntelliSense pro váš projekt. Cesty musí být dostupné pro Visual Studio pro každé rozhraní, na které odkazuje váš projekt Xcode. Průvodce kontroluje odkazy na rozhraní v projektech Xcode a zobrazuje, zda aplikace Visual Studio dokáže najít rozhraní. Všechny cesty, které jste již nastavili v globálních vlastnostech, by měly být zjišťovány sadou Visual Studio. Výjimky jsou uvedeny v seznamu rozhraní. Pro každé rozhraní uvedené s X zadejte cestu dostupnou pro počítač pro Visual Studio, kde najdete rozhraní. Můžete použít tlačítko Procházet **...** a najít cestu pomocí dialogového okna pro **Výběr složky** . Cesta k rozhraní může být buď místní kopie, nebo sdílená složka přístupná přes síť na Macu.

   ![Import z podokna Xcode Frameworks](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "Import z podokna Xcode Frameworks")

   Pokračujte kliknutím na tlačítko **Další** .

1. Podokno **nastavení projektu** umožňuje změnit rozhraní a zahrnout nastavení cesty pro hledání hlaviček pro každý projekt, který průvodce vytvoří. Toto podokno použijte k nastavení cest specifických pro projekt, které se liší od globálních nastavení.

   Chcete-li nastavit cestu pro určitý projekt, vyberte v rozevíracím seznamu **cílový projekt** soubor projektu. Potom nastavte hodnoty v **cestě hledání rozhraní** a zahrňte ovládací prvky pro **cestu pro hledání hlaviček** . Můžete použít tlačítko Procházet **...** vedle každého ovládacího prvku pro vyhledání cesty pomocí dialogového okna pro **Výběr složky** .

   ![Import z podokna projekty Xcode](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "Import z podokna projekty Xcode")

   Pokud se na tomto počítači v aplikaci Visual Studio nespáruje žádná Vzdálená adresa MAC, zobrazí se odkaz **Konfigurace vzdáleného počítače** . Pokyny, jak nastavit párování, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

   Chcete-li importovat projekt Xcode pomocí nastavení průvodce, klikněte na tlačítko **importovat**.

   Průvodce Import z Xcode vytvoří projekty v aplikaci Visual Studio, které odpovídají vybraným cílům projektu Xcode. Kód, který lze sdílet s ostatními C++ projekty, je rozdělen do samostatného sdíleného kódu a statických projektů knihovny. Zbývající kód je umístěn v knihovně iOS a projektech aplikace, které mohou být vytvořeny vzdáleně pomocí aplikace Visual Studio. Další informace o přesouvání kódu mezi Visual Studio a Xcode najdete v tématu [synchronizace změn mezi Xcode a Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [Instalace vývoje mobilních aplikací pro různé platformy pomocíC++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
