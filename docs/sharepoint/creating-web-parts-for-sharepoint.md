---
title: Vytvoření webové části pro službu SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0cbc26a198cace58a957f3d3aaf25457cf457256
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906038"
---
# <a name="create-web-parts-for-sharepoint"></a>Vytvoření webové části pro SharePoint
  Pomocí webových částí můžete upravit obsah, vzhled a chování stránek webu služby SharePoint pomocí prohlížeče. Webové části jsou serverové ovládací prvky, které jsou spouštěny v rámci stránky webových částí: jsou to stavební kameny stránek, které se zobrazí na webu služby SharePoint. Zobrazit [stavebním blokem: webové části](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Můžete vytvářet a ladit webové části na web služby SharePoint pomocí šablon sady Visual Studio.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Vytvoření webové části v sadě Visual Studio
 Vytvoření webové části přidáním **webové části** položky do jakéhokoli projektu SharePoint. Můžete použít **webové části** položky v izolovaném řešení nebo řešení farmy.  
  
 Pokud chcete návrhu webové části vizuálně pomocí designeru, vytvořte **vizuální webové části** projektu nebo přidat **vizuální webové části** položky do jakéhokoli projektu SharePoint. Můžete použít **vizuální webové části** položky v řešení farmy.  
  
### <a name="web-part-item"></a>Položka webové části
 A **webové části** položky obsahuje soubory, které slouží k návrhu webové části webu služby SharePoint. Když přidáte **webové části** položky, sady Visual Studio vytvoří složku ve vašem projektu a přidá několik souborů do složky. Následující tabulka popisuje každý soubor.  
  
|Soubor|Popis|  
|----------|-----------------|  
|*Elements.XML*|Obsahuje informace, které soubor definic funkcí v projektu používá k nasazení webové části.|  
|soubor WebPart|Poskytuje informace, které SharePoint potřebuje ke zobrazení vaší webové části v galerii webových částí.|  
|Soubor kódu|Obsahuje metody, která přidání ovládacích prvků do webové části a který generují vlastní obsah v rámci webové části.|  
  
 Další informace najdete v tématu [postupy: vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Položka vizuální webové části
 Vizuální webová část je webová část, kterou vytvoříte pomocí návrháře Visual Web Developer v sadě Visual Studio. Vizuální webová část funguje stejně jako jiné webové části. Chcete-li přidat ovládací prvky, jako jsou tlačítka a textová pole, do webové části, přidejte kód do souboru XML. Ale přidání ovládacích prvků na vizuální webové části přetažením nebo zkopírováním do webové části ze sady Visual Studio **nástrojů**. Návrhář poté vygeneruje požadovaný kód v souboru XML. Zobrazit [postupy: vytvoření Sharepointovou webovou část pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Ovládací prvky služby SharePoint
 Visual Studio obsahuje některé ovládací prvky pro vytváření stránek služby SharePoint, jako jsou například stránky aplikace. Tyto ovládací prvky se zobrazí v **nástrojů** pod **ovládací prvky SharePoint**. Funkce pro tyto ovládací prvky je odvozena z [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) obor názvů, který obsahuje serverové ovládací prvky ASP.NET použité na stránkách webů a seznamech SharePoint.  
  
|Název ovládacího prvku|Popis|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Vloží nabídku ASP. Další informace najdete v tématu [Přehled ovládacích prvků nabídky](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Vloží **odkaz** elementu do *.aspx* stránce a použije jeden nebo více externích šablon stylů určené **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Vloží ovládací prvek DateTime do *.aspx* stránky.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Vloží ověření zabezpečení do *.aspx* stránky|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Vrátí vlastnost zadaného seznamu.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Vrátí globální vlastnost aktuálního webu.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Vloží odkaz na kanál RSS do *.aspx* stránky.|  
|[Žádost ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Poskytuje vlastnosti a metody pro registraci zdrojů, jako jsou skripty na stránce tak, aby mohly být vyžádány při vykreslování stránky.|  
|[Motiv](http://go.microsoft.com/fwlink/?LinkId=235314)|Použije motiv *.aspx* stránky.|  
  
## <a name="debug-a-web-part"></a>Ladění webové části
 Můžete ladit projekt SharePoint obsahující webovou část, stejně jako by ladění jiných projektů sady Visual Studio. Při spuštění ladicího programu sady Visual Studio, Visual Studio otevře web služby SharePoint.  
  
 Pro spuštění ladění kódu, přidejte webovou část na stránku webových částí služby SharePoint.  
  
 Další informace o tom, jak ladění projektů SharePoint naleznete v tématu [řešení potíží s SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Omezení vizuálních webových částí
 Spouští se v sadě Visual Studio, můžete přidat vizuální webové části do izolovaného prostoru řešení SharePoint a řešení ve farmách. Vizuální webové části však mají následující omezení:  
  
- Vizuální webové části nepodporují nahraditelné parametry. Další informace najdete v tématu [nahraditelné parametry](../sharepoint/replaceable-parameters.md).  
  
- Uživatelské ovládací prvky nebo vizuální části webu nelze přetáhnout a vyřadit ani zkopírovat do vizuálních webových částí. Tato akce způsobí chybu sestavení.  
  
- Vizuální webové části přímo nepodporují tokeny serveru SharePoint, například $SPUrl. Další informace najdete v tématu "Token omezení v izolovaném vizuálních webových tématech" v tématu [řešení potíží s SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
- Vizuální webové části v izolovaném řešení občas zobrazí chyba, "žádost o spuštění izolovaného kódu byla odmítnuta, protože v izolovaném prostoru kód byl příliš zaneprázdněn a nemůže žádost zpracovat." Další informace o této chybě naleznete v tomto příspěvku v [blogu týmu SharePoint Developer](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
- Ladění jazyka JavaScript na straně serveru není podporováno v sadě Visual Studio, ale ladění jazyka JavaScript na straně klienta je podporována.  
  
   I když můžete přidat vložený kód JavaScript do souboru kódu na straně serveru, ladění není podporováno pro zarážky přidané do označení. Chcete-li ladit jazyk JavaScript, odkazovat na externí soubor jazyka JavaScript v souboru označení a potom nastavte body přerušení v souboru jazyka JavaScript.  
  
- Ladění vloženého [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] kódu je třeba provést v souboru generovaného kódu místo v souboru označení.  
  
- Vizuální webové části nepodporují použití `<@ Assembly Src=` směrnice.  
  
- SharePoint webové ovládací prvky a některé [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ovládací prvky nejsou podporovány v izolovaném prostředí služby SharePoint. Pokud jsou používány nepodporované prvky ve vizuální webové části v řešení v izolovaném prostoru, chyba, zobrazí se "Název typu nebo oboru názvů"Motiv"neexistuje v oboru názvů 'Microsoft.SharePoint.WebControls'".  
  
  Další informace o izolovaných řešeních naleznete v tématu [rozdíly mezi řešeními v izolovaném prostoru a ve farmách](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Vytvořit starší styl založený na Sharepointu webové části
 Šablony v sadě Visual Studio můžete použít k vytvoření vlastních [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] webové části pro službu SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] webové části jsou zabudovány nad [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastrukturou webové části a jsou doporučeným typem pro nové projekty.  
  
 V nemnoha případech bude pravděpodobně vytvořit webovou část pomocí staršího stylu webové části založené na Sharepointu. Visual Studio můžete použít k vytvoření těchto typů webových částí, ale Visual Studio neposkytuje žádné šablony, které jsou navrženy speciálně pro jejich vytváření.  
  
 Další informace o při můžete chtít vytvořit starší styl založený na Sharepointu webové části, naleznete v tématu [Infrastruktura webových součástí služby Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Další informace o tom, jak vytvořit webovou část pomocí staršího stylu webové části založené na SharePoint, naleznete v tématu [návod k vytvoření základní webové části služby SharePoint](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Ukazuje, jak vytvořit webové části pro stránky služby SharePoint.|  
|[Postupy: vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Ukazuje, jak vytvořit webové části pro službu SharePoint pomocí návrhové plochy.|  
|[Postupy: vytvoření uživatelského ovládacího prvku pro části stránky nebo webové aplikace služby SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Ukazuje, jak vytvořit vlastní, opakovaně použitelné ovládací prvky, které mohou být spotřebovány stránkami aplikace a webové části, které běží ve službě SharePoint.|  
|[Návod: Vytvoření webové části pro SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Popisuje postup návrhu webové části pro službu SharePoint.|  
|[Návod: Vytvoření webové části pro službu SharePoint pomocí návrháře](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Popisuje postup návrhu webové části pro SharePoint přetažením ovládacích prvků na vizuální návrhovou plochu.|  
|[Návod: Vytvoření webové části Silverlight, která zobrazuje data OData pro službu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Popisuje postup návrhu webové části pro službu SharePoint, který je hostitelem aplikace Silverlight a zobrazuje data ze Sharepointových seznamech.|  
  
