---
title: Konfigurace a platformy pro programové testy UI
ms.date: 2015-10-04
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e4eb09bf1b5477c609dc2b9e3b1502274bc9b931
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894376"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí

V následující tabulce jsou uvedeny podporované konfigurace a platformy pro programové testy uživatelského rozhraní pro Visual Studio Enterprise. Tyto konfigurace platí také pro záznamy akcí vytvořené pomocí [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)].

> [!NOTE]
> Programový test UI musí mít stejná oprávnění jako testovaná aplikace.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

-   Visual Studio Enterprise

## <a name="supported-configurations"></a>Podporované konfigurace

| Konfigurace | Podporováno |
|-| - |
| Operační systémy: | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| Podpora 32bitové/64bitové verze | 32bitová verze Windows, na kterém běží 32bitová verze [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] může testovat 32bitové aplikace.<br /><br /> 64bitová verze Windows, na kterém běží 32bitová verze [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] může testovat 32bitové aplikace subsystému WOW, které mají uživatelské rozhraní Synchronization.n.<br /><br /> 64bitová verze Windows, na kterém běží 32bitová verze [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] můžete otestovat 64bitová verze Windows Forms a aplikace WPF, které nemají uživatelské rozhraní Synchronization.n. |
| Architektura | x86 a x64 **Poznámka:** aplikace Internet Explorer není podporována v 64bitovém režimu s výjimkou spuštění v rámci [!INCLUDE[win8](../debugger/includes/win8_md.md)] nebo novější verze. |
| .NET | .NET 2.0, 3.0, 3.5, 4 a 4.5. **Poznámka:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] a sady Visual Studio vyžadují provoz rozhraní .NET 4. Nicméně aplikace vyvinuté pomocí uvedených verzí rozhraní .NET jsou podporovány. |

> [!NOTE]
> *Uživatelské rozhraní Synchronization.n* je funkce, kde je ověřeno přehrávání ve frontě zpráv každého ovládacího prvku. Pokud ovládací prvek neodpověděl na událost, která mu byla zaslána, událost je odeslána znovu.


## <a name="platform-support"></a>Podpora platforem

| Platforma | Úroveň podpory |
|-| - |
| Aplikace Windows Phone | Pouze WinRT XAML na základě telefonní aplikace jsou podporovány. |
| U aplikací pro UPW | Jsou podporovány pouze aplikace UWP založené na XAML. |
| Univerzální aplikace pro Windows | Jsou podporovány pouze XAML aplikace založené na Universal Windows Phone nebo plochy. |
| Edge | Nahrávání kroků akcí nebo pomocí Tvůrce zobrazíte vlastnosti objektu se nepodporuje. Testy můžete přehrát v prohlížeči Microsoft Edge pomocí Visual Studio 2015 Update 2 a novějších verzích [programového uživatelského rozhraní pro různé prohlížeče testování rozšíření](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting). |
| Internet Explorer 8<br /><br /> Aplikace Internet Explorer 9<br /><br /> Aplikace Internet Explorer 10 **důležité:** aplikace Internet Explorer 10 je podporován pouze na ploše. <br /><br /> Internet Explorer 11 **důležité:** Internet Explorer 11 je podporována pouze na ploše. | Plně podporováno.<br /><br /> -   **Podpora HTML5 v aplikaci Internet Explorer 9 a Internet Explorer 10:** programové testy UI podporují záznam, přehrávání a ověřování ovládacích prvků HTML5: zvuk, Video, indikátor průběhu a posuvník. Další informace najdete v tématu [ovládacích prvků pomocí specifikace HTML5 v programových testů UI](../test/using-html5-controls-in-coded-ui-tests.md). **Upozornění:** Pokud vytvoříte programové testy uživatelského rozhraní v Internet Exploreru 10, se nemusí spustit pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako je Zvuk, Video, Indikátor průběhu a Posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.<br />-   **Podpora pro Internet Explorer 10 pravopisu:** Internet Explorer 10 umožňuje kontrolu pravopisu pro všechna textová pole. Můžete provádět výběr ze seznamu navrhovaných oprav. Programový test UI bude ignorovat akce uživatele, jako je volba návrhu alternativního pravopisu. Bude zaznamenán pouze konečný text zadaný do textového pole.<br />     Tyto akce jsou zaznamenány pro programový test UI používající ovládací prvek kontroly pravopisu: Přidat do slovníku, Kopírovat, Vybrat vše, Přidat do slovníku a Ignorovat.<br />-   **Podpora pro 64bitové aplikace Internet Explorer v systému Windows 8:** dříve nebyly podporovány 64bitové verze aplikace Internet Explorer pro záznam a přehrávání. S [!INCLUDE[win8](../debugger/includes/win8_md.md)] a [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], kódované UI testy povoleny pro 64bitové verze aplikace Internet Explorer. **Upozornění:** 64bitová podpora pro aplikaci Internet Explorer platí, pouze pokud používáte systém [!INCLUDE[win8](../debugger/includes/win8_md.md)] nebo novější.<br />-   **Podpora pro připnuté weby v aplikaci Internet Explorer 9:** v aplikaci Internet Explorer 9 byly zavedeny připnuté weby. Díky funkci Připnuté weby se můžete dostat na své oblíbené weby přímo z hlavního panelu systému Windows – bez nutnosti nejdříve spustit aplikaci Internet Explorer. Programové testy UI nyní mohou generovat akce podporující záměr na připnutých webech. Další informace o připnutých webech naleznete v tématu [připnuté weby](http://go.microsoft.com/fwlink/?LinkId=220037).<br />-   **Podpora pro sémantické značky Internet Explorer 9:** Internet Explorer 9 představuje následující sémantické značky: oddíl, nav, článek, aside, hgroup, záhlaví, zápatí, obrázek, figcaption a značka. Programové testy UI ignorují během záznamu všechny tyto sémantické značky. Pomocí Tvůrce programového testu UI můžete přidat do těchto značek kontrolní výrazy. K procházení všech těchto prvků a zobrazení jejich vlastností můžete použít Navigační vytáčení v Tvůrci programového testu UI.<br />-   **Bezproblémové zpracování prázdných znaků mezi verzemi aplikace Internet Explorer:** existují rozdíly v zacházení s prázdnými znaky mezi aplikace Internet Explorer 8, Internet Explorer 9 a Internet Explorer 10. Programový test UI zpracovává tyto rozdíly bez problémů. Proto se například bude programový test UI vytvořený v aplikaci Internet Explorer 8 přehrávat úspěšně v aplikaci Internet Explorer 9 a Internet Explorer 10.<br />-   **Oznámení oblasti aplikace Internet Explorer je nyní zaznamenána s atributem "Pokračovat na chybu" nastavit:** všechny akce v oznamovací oblasti aplikace Internet Explorer jsou nyní zaznamenávány s nastaveným atributem "Pokračovat na chybu". Pokud se během přehrávání nezobrazí panel oznámení, akce na něm budou ignorovány a programový test UI bude pokračovat další akcí. |
| Ovládací prvky rozhraní Windows Forms a WPF třetích stran | Plně podporováno.<br /><br /> Chcete-li povolit ovládací prvky třetích stran v rozhraních Windows Forms a WPF, musíte přidat odkazy a kód. Další informace najdete v tématu [povolení programového testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md). |
| Aplikace Internet Explorer 6<br /><br /> Internet Explorer 7 | Není podporováno. |
| Chrome<br /><br /> Firefox | Záznam kroků akcí není podporován. Programové testy UI můžete přehrát v prohlížečích Chrome a Firefox, pokud používáte sadu Visual Studio 2012 s aktualizací 4 nebo novější. Přejděte [tady](using-different-web-browsers-with-coded-ui-tests.md) další podrobnosti. |
| Opera<br /><br /> Safari | Není podporováno. |
| Silverlight | Není podporováno.<br /><br /> Pro Visual Studo 2013 však můžete stáhnout [Microsoft Visual Studio 2013 programového modul plug-in testu UI pro technologii Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) z Galerie sady Visual Studio. |
| Flash nebo Java | Není podporováno. |
| Windows Forms 2.0 a vyšší | Plně podporováno. **Poznámka:** ovládací prvky nástrojů NetFx jsou plně podporované, ale ne všechny ovládací prvky třetích stran jsou podporovány. |
| WPF 3.5 a novější | Plně podporováno.<br /><br /> **Poznámka:** ovládací prvky nástrojů NetFx jsou plně podporované, ale ne všechny ovládací prvky třetích stran jsou podporovány. |
| Windows Win32 | Může pracovat s některými známými problémy, ale není oficiálně podporována. |
| MFC | Částečně podporováno. Najdete v článku [UITest framework](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/) podrobnosti o tom, jaké funkce jsou podporovány. |
| SharePoint | Plně podporováno. |
| Klientské aplikace Office | Není podporováno. |
| Webový klient Dynamics CRM | Plně podporováno. |
| Klient Dynamics (Ax) 2012 | Záznam a přehrávání akce jsou podporovány jen částečně. Zobrazit [programového uživatelského rozhraní sady Visual Studio 10 / záznamy akcí podporu pro Microsoft Dynamics](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/) podrobnosti. |
| SAP | Není podporováno. |
| Citrix/Terminálové služby | Nedoporučujeme ale záznam akce na terminálový server. Rekordér nepodporuje spouštění více instancí ve stejnou dobu. |
| PowerBuilder | Částečně podporováno.<br /><br /> Podpora se provádí v rozsahu, ve kterém je povoleno usnadnění pro ovládací prvky aplikace PowerBuilder. |

 Informace o tom, jak vytvořit rozšíření pro podporu jiných platforem, naleznete v tématu [povolení programového testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md) a [rozšířit programových testů UI a záznamů akcí](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Viz také:

- [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)
