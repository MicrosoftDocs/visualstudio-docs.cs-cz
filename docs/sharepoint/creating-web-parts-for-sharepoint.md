---
title: Vytváření Webové části pro SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3825ef7d2c1c90f63a90f5028063c74332543841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015050"
---
# <a name="create-web-parts-for-sharepoint"></a>Vytváření webových částí pro službu SharePoint
  Pomocí webových částí můžete upravit obsah, vzhled a chování stránek webu služby SharePoint pomocí prohlížeče. Webové části jsou ovládací prvky na straně serveru, které běží na stránce webové části: jsou to stavební kameny stránek, které se zobrazují na webu služby SharePoint. Viz [stavební blok: webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Můžete vytvořit a ladit webové části na webu služby SharePoint pomocí šablon ze sady Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Vytvoření webové části v aplikaci Visual Studio
 Chcete-li vytvořit webovou část, přidejte položku **webové části** do libovolného projektu služby SharePoint. Můžete použít položku **webové části** v řešení v izolovaném prostoru nebo v řešení farmy.

 Chcete-li navrhnout webovou část vizuálně pomocí návrháře, vytvořte projekt **vizuální webové části** nebo přidejte položku **vizuální webové části** do libovolného projektu služby SharePoint. Můžete použít položku **vizuální webové části** pouze v řešení farmy.

### <a name="web-part-item"></a>Položka webové části
 Položka **webové části** poskytuje soubory, které lze použít k návrhu webové části pro web služby SharePoint. Když přidáte položku **webové části** , aplikace Visual Studio vytvoří složku v projektu a potom do složky přidá několik souborů. V následující tabulce jsou popsány jednotlivé soubory.

|Soubor|Popis|
|----------|-----------------|
|*Elements.xml*|Obsahuje informace, které soubor definice funkce v projektu používá k nasazení webové části.|
|soubor. WebPart|Poskytuje informace, které SharePoint potřebuje k zobrazení webové části v galerii webových částí.|
|Soubor s kódem|Obsahuje metody, které přidávají ovládací prvky do webové části a generují vlastní obsah v rámci webové části.|

 Další informace najdete v tématu [Postupy: Vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Položka vizuální webové části
 Vizuální webová část je webová část, kterou vytvoříte pomocí návrháře aplikace Visual Web Developer v aplikaci Visual Studio. Vizuální webová část funguje stejně jako jakákoli jiná webová část. Chcete-li přidat ovládací prvky, jako jsou tlačítka a textová pole, do webové části, přidejte kód do souboru XML. Ovládací prvky lze však přidat do vizuální webové části přetažením nebo jejich zkopírováním do webové části v sadě **nástrojů sady**Visual Studio. Návrhář pak vygeneruje požadovaný kód v souboru XML. Viz [Postupy: Vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Ovládací prvky SharePointu
 Visual Studio poskytuje některé ovládací prvky pro vytváření stránek SharePoint, jako jsou například stránky aplikace. Tyto ovládací prvky se zobrazí v **panelu nástrojů** v rámci **ovládacích prvků SharePoint**. Funkce pro tyto ovládací prvky je odvozena z oboru názvů [Microsoft. SharePoint. WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) , který obsahuje ovládací prvky serveru ASP.NET, které se používají na stránkách webu a seznamu služby SharePoint.

|Název ovládacího prvku|Popis|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Vloží nabídku ASP. Další informace najdete v tématu [Přehled ovládacího prvku nabídky](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Vloží element **odkazu** do stránky *aspx* a použije jeden nebo více externích šablon stylů definovaných pomocí **CssRegistration**.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Vloží ovládací prvek DateTime do stránky *aspx* .|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Vloží ověření zabezpečení do stránky *aspx.*|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Vrátí vlastnost zadaného seznamu.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Vrátí globální vlastnost aktuálního webu.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Vloží odkaz na informační kanál RSS do stránky *aspx* .|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Poskytuje vlastnosti a metody pro registraci prostředků, jako jsou skripty, na stránce, aby je bylo možné požadovat při vykreslování stránky.|
|[Motiv](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Použije motiv na stránku *. aspx* .|

## <a name="debug-a-web-part"></a>Ladění webové části
 Můžete ladit projekt služby SharePoint, který obsahuje webovou část, stejně jako byste ladit jiné projekty aplikace Visual Studio. Když spustíte ladicí program sady Visual Studio, Visual Studio otevře web služby SharePoint.

 Chcete-li začít ladit kód, přidejte webovou část na stránku webové části na SharePointu.

 Další informace o tom, jak ladit projekty služby SharePoint, naleznete v tématu [řešení potíží s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Omezení vizuálních webových částí
 Od sady Visual Studio můžete přidat vizuální webové části do izolovaných řešení SharePoint a řešení farmy. Vizuální webové části však mají následující omezení:

- Vizuální webové části nepodporují nahraditelný parametr. Další informace najdete v tématu [nahraditelných parametrů](../sharepoint/replaceable-parameters.md).

- Uživatelské ovládací prvky nebo vizuální webové části nelze přetáhnout a vyřadit nebo zkopírovat do vizuálních webových částí. Tato akce způsobí chybu sestavení.

- Vizuální webové části nepodporují přímo tokeny SharePoint serveru, jako je $SPUrl. Další informace naleznete v tématu "omezení tokenů v izolovaném vizuálu Webové části v tématu [řešení potíží s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Vizuální webové části v řešení v izolovaném prostoru (sandbox) občas obstanou chybu. "žádost o spuštění kódu v izolovaném prostoru byla odmítnuta, protože služba hostitele kódu v izolovaném prostoru byla příliš zaneprázdněna pro zpracování žádosti." Další informace o této chybě najdete v tomto příspěvku na [blogu týmu pro vývojáře SharePointu](https://blogs.msdn.microsoft.com/sharepointdev/2011/02/08/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham/#10149157).

- Ladění JavaScriptu na straně serveru se v aplikaci Visual Studio nepodporuje, ale podporuje se ladění JavaScriptu na straně klienta.

   I když můžete přidat vložený JavaScript do souboru značek na straně serveru, ladění není podporováno pro zarážky přidané do značky. Chcete-li ladit JavaScript, odkazujte na externí soubor JavaScriptu v souboru značek a pak nastavte zarážky v souboru JavaScriptu.

- Ladění vloženého [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] kódu musí být provedeno v souboru generovaného kódu namísto v souboru označení.

- Vizuální webové části nepodporují použití `<@ Assembly Src=` direktivy.

- Webové ovládací prvky SharePointu a některé [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ovládací prvky nejsou podporované v prostředí SharePointu v izolovaném prostoru. Pokud se nepodporované ovládací prvky používají ve vizuální webové části v řešení v izolovaném prostoru (sandbox), zobrazí se chyba "typ nebo název oboru názvů" Theme "v oboru názvů" Microsoft. SharePoint. WebControls "".

  Další informace o řešeních v izolovaném prostoru naleznete v tématu [rozdíly mezi řešeními v izolovaném prostoru a farmách](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Vytvořit starší styl webových částí založených na SharePointu
 Pomocí šablon v aplikaci Visual Studio můžete vytvořit vlastní [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] webové části pro službu SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] webové části jsou postaveny nad [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastrukturou webové části a jsou doporučeným typem pro nové projekty.

 V velmi málo případech může být nutné vytvořit webovou část pomocí webové části starší styl stylů SharePoint. Sadu Visual Studio můžete použít k vytvoření těchto typů webových částí, ale Visual Studio neposkytuje žádné šablony, které jsou navržené speciálně, aby vám pomohly je vytvořit.

 Další informace o tom, kdy možná budete chtít vytvořit starší styl webové části založené na SharePointu, najdete v tématu [Infrastruktura webových částí ve službě Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Další informace o tom, jak vytvořit webovou část pomocí webové části starší styly, najdete v tématu [Postup vytvoření základní webové části služby SharePoint](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Ukazuje, jak vytvořit webové části pro SharePointové stránky.|
|[Postupy: Vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Ukazuje, jak vytvořit webové části pro službu SharePoint pomocí vizuální návrhové plochy.|
|[Postupy: vytvoření uživatelského ovládacího prvku pro stránku aplikace SharePoint nebo webovou část](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Ukazuje, jak vytvořit vlastní, opakovaně použitelné ovládací prvky, které mohou být spotřebovány stránkami aplikace a webovými částmi, které jsou spuštěny v SharePointu.|
|[Návod: Vytvoření webové části pro službu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Popisuje postup návrhu webové části pro službu SharePoint.|
|[Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Popisuje postup návrhu webové části pro službu SharePoint přetažením ovládacích prvků na vizuální návrhovou plochu.|
|[Návod: Vytvoření webové části Silverlight, která zobrazuje OData pro SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Popisuje postup návrhu webové části pro službu SharePoint, která je hostitelem aplikace Silverlight a zobrazuje data ze seznamů služby SharePoint.|
