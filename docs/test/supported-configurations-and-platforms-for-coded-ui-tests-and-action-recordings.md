---
title: Konfigurace a platformy pro programové testy ui
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e18e50537f35080f9796f4a090b3806953ae5170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75845813"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Podporované konfigurace a platformy pro kódované testy a záznamy akcí

Podporované konfigurace a platformy pro kódované testy ui pro Visual Studio Enterprise jsou uvedeny v následující tabulce. Tyto konfigurace platí také pro záznamy [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)]akcí vytvořené pomocí .

> [!NOTE]
> Programový test UI musí mít stejná oprávnění jako testovaná aplikace.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Požadavky**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Podporované konfigurace

| Konfigurace | Podporuje se |
|-| - |
| Operační systémy | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| Podpora 32bitové/64bitové verze | 32bitový systém Windows se systémem [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 32bitový může testovat 32bitové aplikace.<br /><br /> 64bitový systém Windows se systémem [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 32bitový může testovat 32bitové aplikace WOW, které mají soubor Synchronizace ui.n.<br /><br /> 64bitový systém Windows se systémem [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] Windows se systémem 32bitový může testovat 64bitové aplikace systému Windows A WPF, které nemají synchronizaci ui. |
| Architektura | x86 a x64 **Poznámka:** Internet Explorer není podporován v 64bitovém režimu, s výjimkou případů, kdy je spuštěna v podnebo [!INCLUDE[win8](../debugger/includes/win8_md.md)] v novějších verzích. |
| .NET | .NET 2.0, 3.0, 3.5, 4 a 4.5. **Poznámka:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] A Visual Studio bude vyžadovat .NET 4 pro provoz.   Nicméně aplikace vyvinuté pomocí uvedených verzí rozhraní .NET jsou podporovány. |

> [!NOTE]
> *Synchronizace ui* je funkce, kde je přehrávání ověřeno ve frontě zpráv každého ovládacího prvku. Pokud ovládací prvek neodpověděl na událost, která mu byla zaslána, událost je odeslána znovu.

## <a name="platform-support"></a>Podpora platformy

| Platforma | Úroveň podpory |
|-| - |
| Aplikace pro Windows Phone | Podporovány jsou pouze aplikace pro telefony založené na WinRT-XAML. |
| Aplikace pro UPW | Podporovány jsou pouze aplikace UPW založené na XAML. |
| Univerzální aplikace pro Windows | Podporovány jsou pouze univerzální aplikace pro Windows založené na XAML na telefonu a na ploše. |
| Edge | Záznam kroků akce nebo použití tvůrce k zobrazení vlastností objektu není podporováno. Testy lze přehrávat v prohlížeči Edge pomocí Visual Studio 2015 Update 2 a novější verze pomocí [programové rozšíření testování rozhraní a ui cross browser](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting). |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Důležité:** Internet Explorer 10 je podporován pouze na ploše. <br /><br /> Internet Explorer 11 **Důležité:** Internet Explorer 11 je podporován pouze na ploše. | Plně podporováno.<br /><br /> -   **Podpora html5 v aplikaci Internet Explorer 9 a Internet Explorer 10:** Programové testy ui podporují záznam, přehrávání a ověřování ovládacích prvků HTML5: Zvuk, Video, ProgressBar a Slider. Další informace naleznete [v tématu Použití ovládacích prvků HTML5 v kódovaných testech ui](../test/using-html5-controls-in-coded-ui-tests.md). **Upozornění:**      Pokud v aplikaci Internet Explorer 10 vytvoříte kódované testy ui, nemusí být spuštěno pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako je Zvuk, Video, Indikátor průběhu a Posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.<br />-   **Podpora kontroly pravopisu aplikace Internet Explorer 10:** Aplikace Internet Explorer 10 obsahuje funkce kontroly pravopisu pro všechna textová pole. Můžete provádět výběr ze seznamu navrhovaných oprav. Programový test UI bude ignorovat akce uživatele, jako je volba návrhu alternativního pravopisu. Bude zaznamenán pouze konečný text zadaný do textového pole.<br />     Tyto akce jsou zaznamenány pro programový test UI používající ovládací prvek kontroly pravopisu: Přidat do slovníku, Kopírovat, Vybrat vše, Přidat do slovníku a Ignorovat.<br />-   **Podpora 64bitové aplikace Internet Explorer ve Windows 8:** Dříve nebyly pro nahrávání a přehrávání podporovány 64bitové verze aplikace Internet Explorer. S [!INCLUDE[win8](../debugger/includes/win8_md.md)] [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]a , kódované testy ui byly povoleny pro 64bitové verze aplikace Internet Explorer. **Upozornění:** 64bitová podpora aplikace Internet Explorer se [!INCLUDE[win8](../debugger/includes/win8_md.md)] použije pouze v případě, že používáte nebo novější.<br />-   **Podpora připnutých webů v aplikaci Internet Explorer 9:** V aplikaci Internet Explorer 9 byly zavedeny připnuté weby. Díky funkci Připnuté weby se můžete dostat na své oblíbené weby přímo z hlavního panelu systému Windows – bez nutnosti nejdříve spustit aplikaci Internet Explorer. Programové testy UI nyní mohou generovat akce podporující záměr na připnutých webech. Další informace o připnutých webech najdete v tématu [Připnuté weby](https://support.microsoft.com/hub/4230784/internet-explorer-help).<br />-   **Podpora sémantických značek aplikace Internet Explorer 9:** Internet Explorer 9 představil následující sémantické značky: sekce, nav, článek, stranou, hgroup, záhlaví, zápatí, obrázek, fíktitulek a značka. Programové testy UI ignorují během záznamu všechny tyto sémantické značky. Pomocí Tvůrce programového testu UI můžete přidat do těchto značek kontrolní výrazy. K procházení všech těchto prvků a zobrazení jejich vlastností můžete použít Navigační vytáčení v Tvůrci programového testu UI.<br />-   **Bezproblémové zpracování znaků prázdného místa mezi verzemi aplikace Internet Explorer:** Mezi aplikacemi Internet Explorer 8, Internet Explorer 9 a Internet Explorer 10 existují rozdíly ve zpracování znaků prázdného místa. Programový test UI zpracovává tyto rozdíly bez problémů. Proto se například bude programový test UI vytvořený v aplikaci Internet Explorer 8 přehrávat úspěšně v aplikaci Internet Explorer 9 a Internet Explorer 10.<br />-   **Oznamovací oblast aplikace Internet Explorer je nyní zaznamenána sadou atributů Pokračovat při chybě:** Všechny akce v oznamovací oblasti aplikace Internet Explorer jsou nyní zaznamenány pomocí sady atributů Pokračovat při chybě. Pokud se během přehrávání nezobrazí panel oznámení, akce na něm budou ignorovány a programový test UI bude pokračovat další akcí. |
| Ovládací prvky rozhraní Windows Forms a WPF třetích stran | Plně podporováno.<br /><br /> Chcete-li povolit ovládací prvky třetích stran v rozhraních Windows Forms a WPF, musíte přidat odkazy a kód. Další informace naleznete [v tématu Povolení programového testování ovládacích prvků v oblasti řízení](../test/enable-coded-ui-testing-of-your-controls.md). |
| Aplikace Internet Explorer 6<br /><br /> Internet Explorer 7 | Není podporováno. |
| Chrome<br /><br /> Firefox | Záznam kroků akcí není podporován. Programové testy UI můžete přehrát v prohlížečích Chrome a Firefox, pokud používáte sadu Visual Studio 2012 s aktualizací 4 nebo novější. Další [podrobnosti naleznete zde.](using-different-web-browsers-with-coded-ui-tests.md) |
| Opera<br /><br /> Safari | Není podporováno. |
| Silverlight | Není podporováno.<br /><br /> Pro Visual Studo 2013 však můžete stáhnout [Microsoft Visual Studio 2013 kódovaný plugin pro testování ui pro Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) z Galerie Visual Studio. |
| Flash nebo Java | Není podporováno. |
| Windows Forms 2.0 a vyšší | Plně podporováno. **Poznámka:**  Ovládací prvky NetFx jsou plně podporovány, ale ne všechny ovládací prvky třetích stran jsou podporovány. |
| WPF 3.5 a novější | Plně podporováno.<br /><br /> **Poznámka:** Ovládací prvky NetFx jsou plně podporovány, ale ne všechny ovládací prvky třetích stran jsou podporovány. |
| Windows Win32 | Může pracovat s některými známými problémy, ale není oficiálně podporována. |
| MFC | Částečně podporováno. Podrobnosti o tom, jaké funkce jsou podporovány, najdete v [rámci UITest.](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/) |
| SharePoint | Plně podporováno. |
| Klientské aplikace Office | Není podporováno. |
| Webový klient Dynamics CRM | Plně podporováno. |
| Klient Dynamics (Ax) 2012 | Záznam a přehrávání akce jsou podporovány jen částečně. Podrobnosti najdete v tématu [Visual Studio 10 coded UI / action recordings support for Microsoft Dynamics.](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/) |
| SAP | Není podporováno. |
| Citrix/Terminálové služby | Nedoporučujeme zaznamenávat akce na terminálový server. Rekordér nepodporuje spuštění více instancí současně. |
| PowerBuilder | Částečně podporováno.<br /><br /> Podpora se provádí v rozsahu, ve kterém je povoleno usnadnění pro ovládací prvky aplikace PowerBuilder. |

Informace o tom, jak vytvořit rozšíření pro podporu jiných platforem, naleznete [v tématu Povolení programového testování ovládacího rozhraní ovládacích prvků](../test/enable-coded-ui-testing-of-your-controls.md) a [rozšíření kódovaných testů řízení a záznamů akcí](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Viz také

- [Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)
