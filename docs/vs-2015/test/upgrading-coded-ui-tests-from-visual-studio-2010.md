---
title: Upgrade programových testů UI
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a29e531ca9b2a74e67abf80a0e3017a0f5b0b07
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298002"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Upgrade programových testů UI z produktu Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty testů obsahující kódované testy uživatelského rozhraní, které byly vytvořeny v nástroji [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1, jsou při otevření v aplikaci Visual Studio 2012 tiše opraveny. Pokud testovací projekty se změnami do správy zdrojového kódu, soubory projektu jsou rezervovány pro tuto opravu. Po opravě lze tyto testovací projekty obsahující kódované testy uživatelského rozhraní použít v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 i [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Požadavky**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio obsahuje více než jeden typ testovacího projektu. Pokud vytvoříte nový kódovaný test uživatelského rozhraní, vytvoří se v typu projektu programového testu uživatelského rozhraní. Další informace naleznete v tématu [upgrade testů z dřívějších verzí sady Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] projekty testů, které obsahují kódované testy uživatelského rozhraní, musí být znovu sestaveny při otevření testovacího projektu v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nebo [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] vedle sebe [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
> Pokud projekt testu, který byl vytvořen v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] a obsahuje pouze testy jednotek, je otevřen v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], Programový test UI nelze do něj přidat. Podobně nemůžete přidat programový test uživatelského rozhraní do projektu testování částí, který byl vytvořen v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problémy s kompatibilitou mezi Visual Studio 2010 a Visual Studio 2012
 V následující tabulce jsou uvedeny problémy, které je třeba znát při migraci programových testů UI mezi [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] a [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
> Existuje známý problém týkající se odkazy v projekty programového testu UI nezobrazují v Průzkumníku řešení. Další informace najdete v souboru Readme, který je součástí instalačního média [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

|Programové funkce uživatelského rozhraní|Problém|Řešení|
|----------------------------|-----------|--------------|
|V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] se nepodporuje testování uživatelského rozhraní Silverlight.|**Sestavení se nezdaří**<br /><br /> Pokud máte [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 a vytvořili jste projekty programového testu uživatelského rozhraní pro aplikace Silverlight, nelze tyto projekty otevřít v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Doporučujeme spravovat tyto projekty pouze v sadě [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] se nepodporuje testování uživatelského rozhraní Firefox.|**Sestavení proběhne úspěšně, testovací běh selže**<br /><br /> Pokud máte [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 a vytvořili jste projekty programového testu uživatelského rozhraní pro webové aplikace v prohlížeči Firefox, nelze tyto projekty otevřít v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Doporučujeme spravovat tyto projekty pouze v sadě [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2.|
|V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] bylo přidáno nové rozhraní API pro testování kódu uživatelského rozhraní.|**Sestavení se nezdaří**<br /><br /> Pokud vytvoříte kódované testy uživatelského rozhraní pomocí nového rozhraní API pro testování uživatelského rozhraní v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], nelze tyto projekty otevřít v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Projekty používající nové rozhraní API by se měly spravovat jenom v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|
|V [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]byly přidány odkazy v rámci příkazu ' Choose ' v souboru csproj. V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]používáme soubor cíle zpětné vazby, který obsahuje odkazy na sestavení programového testu UI.|V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nelze do testovacího projektu vytvořeného v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (nebo v nástroji SP1) přidat programový test uživatelského rozhraní, který neobsahuje programový test UI (Code).<br /><br /> Proces opravy přidá soubor cílů a zvolit příkaz. Pokud programový test uživatelského rozhraní není v testovacím projektu, projekt je označen jako opravený a při přidání programového testu uživatelského rozhraní do [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nebudou přidány příslušné odkazy.|Budete muset vytvořit nový testovací projekt ve stejném řešení pomocí [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] a přidat nový programový test uživatelského rozhraní do něj. Alternativně můžete přidat kódované testy uživatelského rozhraní do projektu testů v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 a otevřít tento projekt v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

## <a name="UpgradingCodedUIFromVS2010_Update"></a>Aktualizace sady Visual Studio 2010 SP1
 Aktualizace [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 s podporou kompatibility pro Visual Studio 2012 a Windows 8 je k dispozici ke stažení na webu [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=34677) a také jako aktualizace sady Visual Studio.

 Po použití aktualizace jsou pro systém Windows 8 vylepšené funkce programového testu uživatelského rozhraní pro [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1:

- Programový Test uživatelského rozhraní pro Microsoft ovládací prvky založené na rozhraní .NET Framework 4.5 Windows Presentation Foundation (WPF) můžete spustit na počítači se systémem Windows 8.

- Programových testů uživatelského rozhraní pro 64bitovou (x 64) Internet Explorer 10 můžete spustit na počítači se systémem Windows 8.

  Aktualizace taky obsahuje opravy pro následující problémy:

- **Pokrytí kódu:** Nejde otevřít soubor pokrytí kódu (. pokrytí), který je vytvořený v rámci sady Visual Studio 2012 v [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Testovací artefakty v oddílu:** Váš tým má testovací artefakt, který je přiřazen neplatnému uživateli v Team Foundation Server (TFS) 2010. Například uživatel opustí společnost, ale stále má testovacího případu, který je mu přiřazen. Upgrade TFS 2010 na verzi TFS 2012. Použijete [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 pro připojení k upgradovanému serveru TFS. Testovací artefakt nemůžete přiřadit žádnému uživateli TFS pomocí [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Zátěžové testování:** Při spuštění zátěžového testu spolu s jiným typem sítě než s profilem místní sítě (LAN) na počítači s operačním systémem Windows 8 způsobuje ovladač emulátoru sítě selhání operačního systému. Další podrobnosti najdete v [článku 2736182 znalostní báze](https://support.microsoft.com/help/2736182/a-gdr-update-for-visual-studio-2010-sp1-is-available-to-add-compatibil).

## <a name="see-also"></a>Viz také
 [Přenos, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [upgradem testů z předchozích verzí sady Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [použijte automatizaci uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md) [generování programového testu UI z existující akce záznam](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [podporovaných konfigurací a platforem pro programové testy uživatelského rozhraní a záznamy akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
