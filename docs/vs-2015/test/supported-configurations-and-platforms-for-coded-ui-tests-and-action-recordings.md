---
title: Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a záznamy akcí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 946373cc304e4eddb9f724941d583ab653cfe140
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851745"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podporované konfigurace a platformy pro programové testy uživatelského rozhraní pro Visual Studio Enterprise jsou uvedeny v následující tabulce. Tyto konfigurace platí i pro záznamy akcí vytvořené pomocí [!INCLUDE[MTRlong](../includes/mtrlong-md.md)].

> [!NOTE]
> Programový test UI musí mít stejná oprávnění jako testovaná aplikace.

 **Požadavky**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Podporované konfigurace

|Konfigurace|Podporované|
|-------------------|---------------|
|Operační systémy:|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> Windows 10|
|Podpora 32bitové/64bitové verze|32-bitový systém Windows, na kterém běží 32-bit [!INCLUDE[TCMext](../includes/tcmext-md.md)], může testovat 32-bitové aplikace.<br /><br /> 64-bitový systém Windows, na kterém běží 32-bit [!INCLUDE[TCMext](../includes/tcmext-md.md)], může testovat aplikace s 32-bit WOW, které mají uživatelské rozhraní synchronizace. n.<br /><br /> 64-bitový systém Windows, na kterém běží 32-bit [!INCLUDE[TCMext](../includes/tcmext-md.md)], může testovat 64 model Windows Forms a aplikace WPF, které nemají k dispozici synchronizaci uživatelského rozhraní.|
|Architektura|x86 a x64 **Poznámka:** Internet Explorer není podporován v 64ovém režimu s výjimkou spuštění v [!INCLUDE[win8](../includes/win8-md.md)] nebo novějších verzích.|
|.NET|.NET 2.0, 3.0, 3.5, 4 a 4.5. **Poznámka:** [!INCLUDE[TCMext](../includes/tcmext-md.md)] a Visual Studio budou vyžadovat fungování rozhraní .NET 4. Nicméně aplikace vyvinuté pomocí uvedených verzí rozhraní .NET jsou podporovány.|

> [!NOTE]
> *Synchronizace uživatelského rozhraní* je funkce, kde je ověřeno přehrávání ve frontě zpráv každého ovládacího prvku. Pokud ovládací prvek neodpověděl na událost, která mu byla zaslána, událost je odeslána znovu.

## <a name="platform-support"></a>Podpora platformy

|Platforma|Úroveň podpory|
|--------------|----------------------|
|Aplikace Windows Phone|Podporují se jenom telefonní aplikace založené na WinRT-XAML.|
|Aplikace pro Windows Store|Podporovány jsou pouze aplikace pro Windows Store založené na jazyku XAML.|
|Univerzální aplikace pro Windows|Podporují se jenom univerzální aplikace pro Windows založené na jazyce XAML na telefonu a na ploše.|
|Edge|V aplikaci Visual Studio 2015 Update 2 a novější pomocí rozšíření programového [testování uživatelského rozhraní pro různé prohlížeče](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **– Důležité:** Internet Explorer 10 se podporuje jenom na ploše. <br /><br /> Internet Explorer 11 **– Důležité:** Internet Explorer 11 je podporován pouze na ploše.|Plně podporováno.<br /><br /> **Podpora jazyka HTML5 v aplikaci Internet Explorer 9 a Internet Explorer 10:** kódované testy UI podporují záznam, přehrávání a ověřování ovládacích prvků HTML5: zvuk, video, ProgressBar a posuvník. -    Další informace naleznete v tématu [použití ovládacích prvků HTML5 v programových testech UI](../test/using-html5-controls-in-coded-ui-tests.md). **Upozornění:**      Pokud vytvoříte programové testy UI v aplikaci Internet Explorer 10, nemusí být spuštěny pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako je Zvuk, Video, Indikátor průběhu a Posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.<br />-   **Podpora kontroly pravopisu v aplikaci Internet Explorer 10:** Internet Explorer 10 obsahuje možnosti kontroly pravopisu pro všechna textová pole. Můžete provádět výběr ze seznamu navrhovaných oprav. Programový test UI bude ignorovat akce uživatele, jako je volba návrhu alternativního pravopisu. Bude zaznamenán pouze konečný text zadaný do textového pole.<br />     Tyto akce jsou zaznamenány pro programový test UI používající ovládací prvek kontroly pravopisu: Přidat do slovníku, Kopírovat, Vybrat vše, Přidat do slovníku a Ignorovat.<br />**podpora -   pro 64 aplikace Internet Explorer spuštěná v systému Windows 8:** dříve, 64 verze aplikace Internet Explorer pro nahrávání a přehrávání se nepodporují. U [!INCLUDE[win8](../includes/win8-md.md)] a [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]byly v programovém testu UI povoleny 64 verze aplikace Internet Explorer. **Upozornění:** podpora architektury 64 pro Internet Explorer platí pouze v případě, že používáte [!INCLUDE[win8](../includes/win8-md.md)] nebo novější.<br />-   **podporu připnutých webů v aplikaci Internet Explorer 9:** v aplikaci Internet Explorer 9 byly zavedeny připnuté weby. Díky funkci Připnuté weby se můžete dostat na své oblíbené weby přímo z hlavního panelu systému Windows – bez nutnosti nejdříve spustit aplikaci Internet Explorer. Programové testy UI nyní mohou generovat akce podporující záměr na připnutých webech. Další informace o připnuté weby najdete v tématu [připnuté weby](https://windows.microsoft.com/en-US/internet-explorer/products/ie-9/features/pinned-sites).<br />-   **Podpora pro sémantické značky v aplikaci Internet Explorer 9:** aplikace Internet Explorer 9 zavedla následující sémantické značky: oddíl, NAV, článek, zrušení, HGroup, záhlaví, zápatí, obrázek, figcaption a značka. Programové testy UI ignorují během záznamu všechny tyto sémantické značky. Pomocí Tvůrce programového testu UI můžete přidat do těchto značek kontrolní výrazy. K procházení všech těchto prvků a zobrazení jejich vlastností můžete použít Navigační vytáčení v Tvůrci programového testu UI.<br />-   **bezproblémového zpracování prázdných znaků mezi verzemi aplikace Internet Explorer:** existují rozdíly v zacházení s prázdnými znaky mezi Internet Explorer 8, Internet Explorer 9 a Internet Explorer 10. Programový test UI zpracovává tyto rozdíly bez problémů. Proto se například bude programový test UI vytvořený v aplikaci Internet Explorer 8 přehrávat úspěšně v aplikaci Internet Explorer 9 a Internet Explorer 10.<br />-   **oznamovací oblast aplikace Internet Explorer je nyní zaznamenána s nastaveným atributem "pokračovat na chybu":** všechny akce v oznamovací oblasti aplikace Internet Explorer jsou nyní zaznamenávány s nastaveným atributem "pokračovat na chybu". Pokud se během přehrávání nezobrazí panel oznámení, akce na něm budou ignorovány a programový test UI bude pokračovat další akcí.|
|Ovládací prvky rozhraní Windows Forms a WPF třetích stran|Plně podporováno.<br /><br /> Chcete-li povolit ovládací prvky třetích stran v rozhraních Windows Forms a WPF, musíte přidat odkazy a kód. Další informace naleznete v tématu [Povolení programového testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md).|
|Internet Explorer 6<br /><br /> Internet Explorer 7|Není podporováno.|
|Chrome<br /><br /> Firefox|Záznam kroků akcí není podporován. Programové testy UI můžete přehrát v prohlížečích Chrome a Firefox, pokud používáte sadu Visual Studio 2012 s aktualizací 4 nebo novější. Další podrobnosti najdete [zde](https://msdn.microsoft.com/library/jj835758.aspx).|
|Opera<br /><br /> Safari|Není podporováno.|
|Silverlight|Není podporováno.<br /><br /> Pro Visual Studo 2013 však můžete stáhnout [modul plug-in programového testu uživatelského rozhraní Microsoft Visual Studio 2013 pro program Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) z galerie sady Visual Studio.|
|Flash nebo Java|Není podporováno.|
|Windows Forms 2.0 a vyšší|Plně podporováno. **Poznámka:**  Ovládací prvky NetFx jsou plně podporovány, ale ne všechny ovládací prvky třetích stran jsou podporovány.|
|WPF 3.5 a novější|Plně podporováno.<br /><br /> **Poznámka:** Ovládací prvky NetFx jsou plně podporovány, ale ne všechny ovládací prvky třetích stran jsou podporovány.|
|Windows Win32|Může pracovat s některými známými problémy, ale není oficiálně podporována.|
|MFC|Částečně podporováno. Podrobnosti o podporovaných funkcích najdete na následujícím webu [společnosti Microsoft](https://blogs.msdn.com/b/vstsqualitytools/archive/2010/04/15/uitest-framework-mfc-support-in-vs-2010.aspx) .|
|SharePoint|Plně podporováno.|
|Klientské aplikace Office|Není podporováno.|
|Webový klient Dynamics CRM|Plně podporováno.|
|Klient Dynamics (Ax) 2012|Záznam a přehrávání akce jsou podporovány jen částečně. Podrobnosti najdete na následujícím webu [společnosti Microsoft](https://blogs.msdn.com/b/dave_froslie/archive/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012.aspx) .|
|SAP|Není podporováno.|
|Citrix/Terminálové služby|Nedoporučujeme nahrávat akce na terminálový server. Zapisovač nepodporuje spouštění více instancí současně.|
|PowerBuilder|Částečně podporováno.<br /><br /> Podpora se provádí v rozsahu, ve kterém je povoleno usnadnění pro ovládací prvky aplikace PowerBuilder.|

 Informace o tom, jak vytvořit rozšíření pro podporu jiných platforem, naleznete v tématu Povolení programového [testování uživatelského rozhraní pro vaše ovládací prvky](../test/enable-coded-ui-testing-of-your-controls.md) a rozšíření programových [testů uživatelského rozhraní a záznamů akcí pro podporu aplikace Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Viz také
 [Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md) [generování programového testu uživatelského rozhraní z existujícího záznamu akce](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
