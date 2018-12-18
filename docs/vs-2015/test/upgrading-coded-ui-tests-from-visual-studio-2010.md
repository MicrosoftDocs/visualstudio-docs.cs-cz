---
title: Upgrade programových testů UI
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-devops-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: gewarren
manager: douge
ms.openlocfilehash: 664eeb618b92b7d3181a223a531aac02e046ab0f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055047"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Upgrade programových testů UI z produktu Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testovací projekty obsahující programové testy uživatelského rozhraní, které byly vytvořeny v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 jsou opravena bezobslužná při otevření v sadě Visual Studio 2012. Pokud testovací projekty se změnami do správy zdrojového kódu, soubory projektu jsou rezervovány pro tuto opravu. Po opravě těchto testovací projekty obsahující kódované UI testy lze pak použít v obou [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 a [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Požadavky**

-   Visual Studio Enterprise

> [!NOTE]
>  Visual Studio obsahuje více než jeden typ testovacího projektu. Pokud vytvoříte nový kódovaný test uživatelského rozhraní, vytvoří se v typu projektu programového testu uživatelského rozhraní. Další informace najdete v tématu [upgradování testů ze starších verzí sady Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
>  [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] projekty testů, které obsahují programové testy UI musí znovu vytvořit při otevření projektu testu v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nebo [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] – souběžně s [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
>  Pokud testovací projekt, který byl vytvořen v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] a obsahuje pouze test jednotek je otevřen v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]jsou kódované testy uživatelského rozhraní nelze přidat k němu. Podobně nelze přidat programový test uživatelského rozhraní pro projekt testování částí, který byl vytvořen v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problémy s kompatibilitou mezi Visual Studio 2010 a Visual Studio 2012
 V následující tabulce jsou uvedené problémy, které je potřeba vědět při migraci kódované testy uživatelského rozhraní mezi [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] a [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
>  Existuje známý problém týkající se odkazy v projekty programového testu UI nezobrazují v Průzkumníku řešení. Další informace najdete v souboru ReadMe na [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] instalačního média.

|Programové funkce uživatelského rozhraní|Problém|Řešení|
|----------------------------|-----------|--------------|
|Testování uživatelského rozhraní Silverlight se nepodporuje v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Sestavení se nezdaří**<br /><br /> Pokud máte [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] funkce aktualizací Service Pack 2 a jste vytvořili projekty testů programového uživatelského rozhraní pro aplikace Silverlight, nelze jej tyto projekty otevřít v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Doporučujeme, abyste při správě těchto projektů v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] pouze funkce aktualizací Service Pack 2.|
|Testování uživatelského rozhraní pro Firefox nepodporuje [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Sestavení proběhne úspěšně, testovacího běhu se nezdaří.**<br /><br /> Pokud máte [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] funkce aktualizací Service Pack 2 a jste vytvořili projekty testů programového uživatelského rozhraní pro webové aplikace v aplikaci Firefox, těchto projektů lze otevřít pouze v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Doporučujeme, abyste při správě těchto projektů v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] pouze funkce aktualizací Service Pack 2.|
|Nový kód uživatelského rozhraní testování rozhraní API se přidaly do [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Sestavení se nezdaří**<br /><br /> Pokud vytvoříte programové testy uživatelského rozhraní pomocí nového uživatelského rozhraní testování rozhraní API v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], nelze tyto projekty otevřít v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Projektů pomocí nového rozhraní API se mají spravovat v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] pouze.|
|V [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], byly přidány odkazy uvnitř příkazu "Zvolit" v souboru csproj. V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], používáme soubor cílů zpětnou vazbu odkazy programového sestavení uživatelského rozhraní testu.|V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], programový Test uživatelského rozhraní nelze přidat do projektu testů vytvořené v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (nebo s aktualizací SP1), která neobsahovala programový Test uživatelského rozhraní.<br /><br /> Proces opravy přidá soubor cílů a zvolit příkaz. Pokud programový Test uživatelského rozhraní není v projektu testu a projekt je označen jako opravit a příslušných odkazů nebudou přidány, při přidávání programový Test uživatelského rozhraní v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Budete muset vytvořit nový testovací projekt ve stejném řešení pomocí [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] a přidat váš nový programový Test uživatelského rozhraní. Alternativně můžete přidat programové testy uživatelského rozhraní do testovacího projektu ve [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 a otevřete projekt, který v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 SP1 Update
 Aktualizace [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 s podporou kompatibility pro Visual Studio 2012 a Windows 8 je k dispozici ke stažení na [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=34677) a aktualizovat také jako sady Visual Studio.

 Po instalaci aktualizace, následující [!INCLUDE[vs2010](../includes/vs2010-md.md)] lepší programové funkce nástroj pro testování uživatelského rozhraní pro Windows 8 s aktualizací SP1:

- Programový Test uživatelského rozhraní pro Microsoft ovládací prvky založené na rozhraní .NET Framework 4.5 Windows Presentation Foundation (WPF) můžete spustit na počítači se systémem Windows 8.

- Programových testů uživatelského rozhraní pro 64bitovou (x 64) Internet Explorer 10 můžete spustit na počítači se systémem Windows 8.

  Aktualizace taky obsahuje opravy pro následující problémy:

- **Pokrytí kódu:** neschopnost otevřít soubor pokrytí kódu (.coverage), který je vytvořen pomocí sady Visual Studio 2012 v [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Bezvýchodná situace testovacích artefaktů:** test artefaktu, který je přiřazen k neplatný uživatel v Team Foundation Server (TFS) 2010 má váš tým. Například uživatel opustí společnost, ale stále má testovacího případu, který je mu přiřazen. Upgrade TFS 2010 na verzi TFS 2012. Použijete [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 pro připojení k upgradovaném serveru TFS. Nejste schopni přiřazení artefaktů testu pro všechny uživatele TFS pomocí [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Zátěžové testování:** při spuštění zátěžového testu společně s typem sítě než profil místní sítě (LAN) na počítači, to se systémem Windows 8, ovladač emulace sítě způsobí, že operační systém při selhání. Další podrobnosti najdete v tématu [2736182 článku znalostní BÁZE](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Viz také
 [Přenosy, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [upgradování testů ze starších verzí sady Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md) [generování Programový Test uživatelského rozhraní ze stávajícího záznamu akcí](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
