---
title: Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: gewarren
manager: douge
ms.openlocfilehash: 23c1c84180df7fd185ce29d265f89c6b905ff794
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198767"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Podporované konfigurace a platformy pro programové testy uživatelského rozhraní a zaznamenávání akcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V následující tabulce jsou uvedeny podporované konfigurace a platformy pro programové testy uživatelského rozhraní pro Visual Studio Enterprise. Tyto konfigurace platí také pro záznamy akcí vytvořené pomocí [!INCLUDE[MTRlong](../includes/mtrlong-md.md)].  
  
> [!NOTE]
>  Programový test UI musí mít stejná oprávnění jako testovaná aplikace.  
  
 **Požadavky**  
  
-   Visual Studio Enterprise  
  
## <a name="supported-configurations"></a>Podporované konfigurace  
  
|Konfigurace|Podporováno|  
|-------------------|---------------|  
|Operační systémy:|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> Windows 10|  
|Podpora 32bitové/64bitové verze|32bitová verze Windows, na kterém běží 32bitová verze [!INCLUDE[TCMext](../includes/tcmext-md.md)] může testovat 32bitové aplikace.<br /><br /> 64bitová verze Windows, na kterém běží 32bitová verze [!INCLUDE[TCMext](../includes/tcmext-md.md)] může testovat 32bitové aplikace subsystému WOW, které mají uživatelské rozhraní Synchronization.n.<br /><br /> 64bitová verze Windows, na kterém běží 32bitová verze [!INCLUDE[TCMext](../includes/tcmext-md.md)] můžete otestovat 64bitová verze Windows Forms a aplikace WPF, které nemají uživatelské rozhraní Synchronization.n.|  
|Architektura|x86 a x64 **Poznámka:** aplikace Internet Explorer není podporována v 64bitovém režimu s výjimkou spuštění v rámci [!INCLUDE[win8](../includes/win8-md.md)] nebo novější verze.|  
|.NET|.NET 2.0, 3.0, 3.5, 4 a 4.5. **Poznámka:** [!INCLUDE[TCMext](../includes/tcmext-md.md)] a sady Visual Studio vyžadují provoz rozhraní .NET 4. Nicméně aplikace vyvinuté pomocí uvedených verzí rozhraní .NET jsou podporovány.|  
  
> [!NOTE]
>  *Uživatelské rozhraní Synchronization.n* je funkce, kde je ověřeno přehrávání ve frontě zpráv každého ovládacího prvku. Pokud ovládací prvek neodpověděl na událost, která mu byla zaslána, událost je odeslána znovu.  
  
## <a name="platform-support"></a>Podpora platformy  
  
|Platforma|Úroveň podpory|  
|--------------|----------------------|  
|Aplikace Windows Phone|Pouze WinRT XAML na základě telefonní aplikace jsou podporovány.|  
|Aplikace pro Windows Store|Podporovány jsou pouze aplikace pro Windows Store založené na jazyku XAML.|  
|Univerzální aplikace pro Windows|Jsou podporovány pouze XAML aplikace založené na Universal Windows Phone nebo plochy.|  
|Edge|V aplikaci Visual Studio 2015 Update 2 a vyšší s využitím [kódované UI Cross Browser Testing rozšíření](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|  
|Internet Explorer 8<br /><br /> Aplikace Internet Explorer 9<br /><br /> Aplikace Internet Explorer 10 **důležité:** aplikace Internet Explorer 10 je podporován pouze na ploše. <br /><br /> Internet Explorer 11 **důležité:** Internet Explorer 11 je podporována pouze na ploše.|Plně podporováno.<br /><br /> -   **Podpora HTML5 v aplikaci Internet Explorer 9 a Internet Explorer 10:** programové testy UI podporují záznam, přehrávání a ověřování ovládacích prvků HTML5: zvuk, Video, indikátor průběhu a posuvník. Další informace najdete v tématu [pomocí ovládacích prvků HTML5 v programových testů uživatelského rozhraní](../test/using-html5-controls-in-coded-ui-tests.md). **Upozornění:** Pokud vytvoříte programové testy uživatelského rozhraní v Internet Exploreru 10, se nemusí spustit pomocí aplikace Internet Explorer 9 nebo Internet Explorer 8. Je to proto, že aplikace Internet Explorer 10 obsahuje ovládací prvky HTML5, jako je Zvuk, Video, Indikátor průběhu a Posuvník. Tyto ovládací prvky jazyka HTML5 nejsou rozpoznány aplikací Internet Explorer 9 nebo Internet Explorer 8. Podobně váš programový test UI pomocí aplikace Internet Explorer 9 může zahrnovat některé ovládací prvky jazyka HTML5, které aplikace Internet Explorer 8 nerozpozná.<br />-   **Podpora pro Internet Explorer 10 pravopisu:** Internet Explorer 10 umožňuje kontrolu pravopisu pro všechna textová pole. Můžete provádět výběr ze seznamu navrhovaných oprav. Programový test UI bude ignorovat akce uživatele, jako je volba návrhu alternativního pravopisu. Bude zaznamenán pouze konečný text zadaný do textového pole.<br />     Tyto akce jsou zaznamenány pro programový test UI používající ovládací prvek kontroly pravopisu: Přidat do slovníku, Kopírovat, Vybrat vše, Přidat do slovníku a Ignorovat.<br />-   **Podpora pro 64bitové aplikace Internet Explorer v systému Windows 8:** dříve nebyly podporovány 64bitové verze aplikace Internet Explorer pro záznam a přehrávání. S [!INCLUDE[win8](../includes/win8-md.md)] a [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kódované UI testy povoleny pro 64bitové verze aplikace Internet Explorer. **Upozornění:** 64bitová podpora pro aplikaci Internet Explorer platí, pouze pokud používáte systém [!INCLUDE[win8](../includes/win8-md.md)] nebo novější.<br />-   **Podpora pro připnuté weby v aplikaci Internet Explorer 9:** v aplikaci Internet Explorer 9 byly zavedeny připnuté weby. Díky funkci Připnuté weby se můžete dostat na své oblíbené weby přímo z hlavního panelu systému Windows – bez nutnosti nejdříve spustit aplikaci Internet Explorer. Programové testy UI nyní mohou generovat akce podporující záměr na připnutých webech. Další informace o připnutých webech naleznete v tématu [připnuté weby](http://go.microsoft.com/fwlink/?LinkId=220037).<br />-   **Podpora pro sémantické značky Internet Explorer 9:** Internet Explorer 9 představuje následující sémantické značky: oddíl, nav, článek, aside, hgroup, záhlaví, zápatí, obrázek, figcaption a značka. Programové testy UI ignorují během záznamu všechny tyto sémantické značky. Pomocí Tvůrce programového testu UI můžete přidat do těchto značek kontrolní výrazy. K procházení všech těchto prvků a zobrazení jejich vlastností můžete použít Navigační vytáčení v Tvůrci programového testu UI.<br />-   **Bezproblémové zpracování prázdných znaků mezi verzemi aplikace Internet Explorer:** existují rozdíly v zacházení s prázdnými znaky mezi aplikace Internet Explorer 8, Internet Explorer 9 a Internet Explorer 10. Programový test UI zpracovává tyto rozdíly bez problémů. Proto se například bude programový test UI vytvořený v aplikaci Internet Explorer 8 přehrávat úspěšně v aplikaci Internet Explorer 9 a Internet Explorer 10.<br />-   **Oznámení oblasti aplikace Internet Explorer je nyní zaznamenána s atributem "Pokračovat na chybu" nastavit:** všechny akce v oznamovací oblasti aplikace Internet Explorer jsou nyní zaznamenávány s nastaveným atributem "Pokračovat na chybu". Pokud se během přehrávání nezobrazí panel oznámení, akce na něm budou ignorovány a programový test UI bude pokračovat další akcí.|  
|Ovládací prvky rozhraní Windows Forms a WPF třetích stran|Plně podporováno.<br /><br /> Chcete-li povolit ovládací prvky třetích stran v rozhraních Windows Forms a WPF, musíte přidat odkazy a kód. Další informace najdete v tématu [povolit kódované UI Testing of Your Controls](../test/enable-coded-ui-testing-of-your-controls.md).|  
|Aplikace Internet Explorer 6<br /><br /> Internet Explorer 7|Není podporováno.|  
|Chrome<br /><br /> Firefox|Záznam kroků akcí není podporován. Programové testy UI můžete přehrát v prohlížečích Chrome a Firefox, pokud používáte sadu Visual Studio 2012 s aktualizací 4 nebo novější. Přejděte [tady](http://msdn.microsoft.com/library/jj835758.aspx) další podrobnosti.|  
|Opera<br /><br /> Safari|Není podporováno.|  
|Silverlight|Není podporováno.<br /><br /> Pro Visual Studo 2013 však můžete stáhnout [Microsoft Visual Studio 2013 programového modul plug-in testu UI pro technologii Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) z Galerie sady Visual Studio.|  
|Flash nebo Java|Není podporováno.|  
|Windows Forms 2.0 a vyšší|Plně podporováno. **Poznámka:** ovládací prvky nástrojů NetFx jsou plně podporované, ale ne všechny ovládací prvky třetích stran jsou podporovány.|  
|WPF 3.5 a novější|Plně podporováno.<br /><br /> **Poznámka:** ovládací prvky nástrojů NetFx jsou plně podporované, ale ne všechny ovládací prvky třetích stran jsou podporovány.|  
|Windows Win32|Může pracovat s některými známými problémy, ale není oficiálně podporována.|  
|MFC|Částečně podporováno. Přečtěte si následující [webu společnosti Microsoft](http://go.microsoft.com/fwlink/?LinkId=206511) podrobnosti o tom, jaké funkce jsou podporovány.|  
|SharePoint|Plně podporováno.|  
|Klientské aplikace Office|Není podporováno.|  
|Webový klient Dynamics CRM|Plně podporováno.|  
|Klient Dynamics (Ax) 2012|Záznam a přehrávání akce jsou podporovány jen částečně. Přečtěte si následující [webu společnosti Microsoft](http://go.microsoft.com/fwlink/?LinkId=232677) podrobnosti.|  
|SAP|Není podporováno.|  
|Citrix/Terminálové služby|Nedoporučujeme ale záznam akce na terminálový server. Rekordér nepodporuje spouštění více instancí ve stejnou dobu.|  
|PowerBuilder|Částečně podporováno.<br /><br /> Podpora se provádí v rozsahu, ve kterém je povoleno usnadnění pro ovládací prvky aplikace PowerBuilder.|  
  
 Informace o tom, jak vytvořit rozšíření pro podporu jiných platforem, naleznete v tématu [povolit kódované UI Testing of Your Controls](../test/enable-coded-ui-testing-of-your-controls.md) a [rozšiřování programových testů uživatelského rozhraní a zaznamenávání akcí pro podporu Microsoft Excelu](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)   
 [Generování programového testu UI ze stávajícího záznamu akcí](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)



