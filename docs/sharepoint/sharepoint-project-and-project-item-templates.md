---
title: Šablony položek projektu služby SharePoint a Project | Dokumentace společnosti Microsoft
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e38a3e709a8d49d29d598e7eabd55e7be154836
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896442"
---
# <a name="sharepoint-project-and-project-item-templates"></a>A šablony položek projektu služby SharePoint
  Následující části popisují dostupné projektu služby SharePoint a položky projektu, šablony a způsobu jejich použití. 
  
## <a name="project-and-project-item-templates-overview"></a>Projekt a Přehled šablon položek projektu
 Když vytvoříte nový projekt služby SharePoint v sadě Visual Studio, SharePoint projekt je přidán do řešení společně se všechny položky projektu vyžaduje tento typ projektů. Například pokud vytvoříte projekt webové části Silverlight, Visual Studio vytvoří řešení, které obsahuje položky projektu vizuální webové části a položky projektu Silverlight aplikace spolu se všechny soubory, které vyžadují tyto položky projektu. Šablony položek projektu se používají k přidání položky projektu do existujícího projektu služby SharePoint, jako je například přidání příjemce událostí, sloupec nebo seznamu.  
  
 Informace o základech služby SharePoint, naleznete v tématu [SharePoint Foundation stavební bloky](http://go.microsoft.com/fwlink/?LinkId=179404). Pokročilí uživatelé mohou vytvářet vlastních projektů a šablon položek projektu. Další informace najdete v tématu [rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
## <a name="project-templates"></a>Šablony projektů
 Tady je seznam šablon projektu služby SharePoint. K zobrazení šablon projektu služby SharePoint v sadě Visual Studio, v **nový projekt** dialogového okna rozbalte **SharePoint** uzlu buď **Visual C#**  nebo  **Visual Basic**a klikněte na tlačítko **2010**.  
  
### <a name="sharepoint-2010-project"></a>Projekt SharePoint 2010
 Obsah *projektu služby SharePoint 2010* jsou zahrnuty v každé šabloně projektu služby SharePoint. Projekt služby SharePoint 2010 obsahuje:  
  
-   Soubor projektu.  
  
-   Stránce vlastností projektu.  
  
-   A **odkazy** složky obsahující všechny odkazy na sestavení v projektu.  
  
-   A **funkce** složku, která obsahuje *.feature* konfigurační soubor, použít k nasazení funkcí na SharePoint server.  
  
-   A **balíčku** složku, která obsahuje *Package.package* soubor používá k nasazení řešení služby SharePoint.  
  
-   Soubor klíč.snk (klíč se silným názvem), který se používá k podepsání sestavení silným názvem pro zvýšené zabezpečení.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>Webové části technologie Silverlight v Sharepointu 2010
 *Webové části služby SharePoint 2010 Silverlight* projektů vám umožní vytvořit webové části pro SharePoint, která se zobrazí aplikace Silverlight. Když vytvoříte tento projekt, můžete určit, zda chcete přidat novou aplikaci Silverlight k němu nebo odkazovat na existující. Další informace najdete v tématu [vytvořit webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) a [návod: vytvoření webové části Silverlight, která zobrazuje data OData pro službu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Vizuální webové části služby SharePoint 2010
 A *Sharepointu 2010 vizuální webová část* projekt obsahuje *Elements.xml* soubor definice **webové části** položky a **uživatelský ovládací prvek** položky . Přetažením nebo zkopírováním ovládacích prvků na plochu uživatelského ovládacího prvku z panelu nástrojů sady Visual Studio můžete navrhnout vzhled vizuální webové části. Další informace najdete v tématu [postupy: vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) a [stavebním blokem: webové části](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>Importovat balíček řešení služby SharePoint 2010
 *Importovat balíček řešení služby SharePoint 2010* projekty umožňují importovat nebo její část existujícího webu SharePoint 2010, exportovat do řešení služby SharePoint (*.wsp*) soubor do sady Visual Studio. Po naimportování do sady Visual Studio, můžete přizpůsobit jeho položky a znovu nasadit. Další informace najdete v tématu [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Import opakovaně použitelného pracovního postupu služby SharePoint 2010
 *Import opakovaně použitelného pracovního postupu služby SharePoint 2010* projekty umožňují importovat deklarativní, opakovaně použitelný pracovní postup vytvořený v Návrháři SharePoint 2010 do sady Visual Studio. Pracovní postup se exportuje z webu služby SharePoint jako *.wsp* souboru. Po naimportování do sady Visual Studio, můžete ji přizpůsobit, přidejte do ní kód a nasadit ho na Sharepointový Web. Další informace najdete v tématu [návod: Import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
## <a name="project-item-templates"></a>Šablony položek projektu
 Tady je seznam šablon položek projektu služby SharePoint. Šablony položek projektu přidejte soubory do řešení služby SharePoint pro podporu funkcí služby SharePoint, jako je například sloupců webu, seznamy a typy obsahu. Například přidání sloupce webu do řešení přidá projektu sloupce webu, který obsahuje *Elements.xml* definičního souboru. Přidání vizuální webové části přidá do vašeho řešení, která obsahuje projektu vizuální webové části *Elements.xml* souboru, položku ovládacího prvku uživatel a položka vizuální webové části.  
  
 Chcete-li zobrazit šablony položek projektu služby SharePoint, v **Průzkumníka řešení**, otevřete místní nabídku pro projekt služby SharePoint a klikněte na tlačítko **přidat**, **nová položka**. Rozbalte **SharePoint** uzlu buď **Visual C#**  nebo **jazyka Visual Basic**a klikněte na tlačítko **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Stránka aplikace (pouze řešení farmy)
 **Stránka aplikace (pouze řešení farmy)** položky umožňuje návrh [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] webovou stránku webu služby SharePoint. Stránky aplikací můžete použít jenom v řešení farmy. Tuto položku projektu můžete přidat pouze řešení farmy. Další informace najdete v tématu [postupy: vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md) a [_layouts aplikace typ stránky](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Model připojení obchodních dat (pouze řešení farmy)
 A **Model Připojení obchodních dat (pouze řešení farmy)** položky umožňuje integrace obchodních dat do služby SharePoint. Obchodní data můžou pocházet z back endové serverové aplikace, jako například [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel a reklamní SAP Service Protocol (). Modelů připojení obchodních dat lze použít pouze v řešení farmy. Tuto položku projektu můžete přidat pouze řešení farmy. Další informace najdete v tématu [postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md), [postupy: použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), a [co je nového: Připojení obchodních Služby](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Typ obsahu
 *Typ obsahu* položek vám umožní vytvořit vlastní typy obsahu, které jsou založené na stávající typ (základní) obsahu například dokument, oznámení nebo úkolu. Vlastní typ obsahu poskytuje stejné atributy a pole jako základní typ obsahu spolu s všechny sloupce webu (pole) můžete definovat. Například můžete vytvořit vlastní kontakt typu obsahu, který je založen na základní kontakt typ obsahu, která se dodává v Sharepointu. Typ obsahu můžete přizpůsobit změnou existující sloupce webu nebo přidat další sloupce webu k těm, které jsou již zahrnuty v základním typu obsahu.  
  
> [!NOTE]  
>  Kvůli omezením služby SharePoint nelze vytvořit typ obsahu řešení farmy podle typu obsahu řešení v izolovaném prostoru.  
  
 Další informace najdete v tématu [návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) a [stavebním blokem: typ obsahu](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Prázdný element
 *Prázdný element* se nejčastěji používají k definování položek projektu služby SharePoint, které nemají projekt nebo šablonu položky projektu v sadě Visual Studio. Když přidáte do svého projektu prázdný element, uzel s názvem EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] obsahuje jediný soubor, který je pojmenovaná *Elements.xml.* Použití [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] příkazy k definování požadované prvky v *Elements.xml*.  
  
### <a name="event-receiver"></a>Příjemce událostí
 *Přijímače událostí* zpracovávat události pro položky na Sharepointovém webu, například při přidání položky do seznamu, když se odstraní položka webové nebo při spuštění pracovního postupu. Šablony položky projektu příjemce událostí umožňuje zpracovat  
  
- Události seznamu  
  
- Události položek seznamu  
  
- E-mailové události seznamu  
  
- Události webu  
  
- Události pracovního postupu seznamu  
  
  Vytvoří projekt položka přijímače události **příjemce událostí** složky souborem jednu třídu, která obsahuje obslužné rutiny událostí pro všechny události, které jste zadali při vytváření projektu v **přizpůsobení Sharepointu Průvodce**. Přijímače událostí můžete zpracovávat události, ke kterým dochází na webu služby SharePoint, když položky, jako jsou soubory, pole, položky, seznamy, přílohy, webové části a pracovních postupů se přidá, aktualizovat, odstranit nebo odebrat. Další informace najdete v tématu [postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md) a [stavebním blokem: zpracování událostí](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>Seznam  
 Seznam je instance opakovaně použitelné základní definici seznamu SharePoint, jako je kalendář nebo seznamu úloh. Po přidání seznamu do vašeho řešení, Návrhář seznamu můžete přidat do seznamu sloupců webu a vytvořte vlastní seznam sloupců. To zahrnuje sloupce webu z typy obsahu. Můžete zadat *zobrazení* pro seznam, který určuje, které se zobrazí v seznamu sloupců. Další informace najdete v tématu [návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) a [stavebním blokem: seznamy a knihovny dokumentů](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Modul  
 *Moduly* (Nezaměňovat s [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduly) obsahují všechny soubory, které chcete nasadit na server SharePoint, jako jsou obrázky nebo poznámky. Položka modulu projektu obsahuje **modulu** uzlu. Uzel modulu obsahuje dvě šablony položek projektu: soubor definice XML, který se chová jako manifest pro modul, a *ukázka.txt* zástupného symbolu, soubor. Další informace najdete v tématu [modulů použití vložených souborů v řešení](../sharepoint/using-modules-to-include-files-in-the-solution.md) a [moduly](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Sekvenčního pracovního postupu (pouze řešení farmy)
 A *sekvenčního pracovního postupu* je posloupnost kroků obchodní logiky, provádějí v pořadí, dokud není dokončena poslední krok. Sekvenční pracovní postupy se používají ke správě procesy, které se týkají položek služby SharePoint, jako jsou seznamy a dokumenty. Můžete vytvořit pracovní postupy (globální) úrovni webu nebo seznamu úroveň (místní) pracovních postupů a můžete vybrat, jestli spuštění pracovního postupu automaticky nebo ručně. Tuto položku projektu lze použít pouze v řešení farmy. Tuto položku projektu můžete přidat pouze řešení farmy. Další informace najdete v tématu [řešení pracovního postupu Sharepointu vytvořit](../sharepoint/creating-sharepoint-workflow-solutions.md), [pracovních postupů v produktu SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), a [What's New: Vylepšení pracovního postupu](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Webová část Silverlight
 *Webová část Silverlight* položky projektu vám umožní vytvořit webové části pro SharePoint, která se zobrazí aplikace Silverlight. Když přidáte tuto položku projektu do řešení, můžete nastavit, jestli se má přidat novou aplikaci Silverlight nebo některý z existujících později odkazovat. Další informace najdete v tématu [vytvořit webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) a [návod: vytvoření webové části Silverlight, která zobrazuje data OData pro službu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Sloupec webu
 A *sloupce webu*, označované také jako *pole*, je jedním z nejzákladnějších prvků můžete přidat do projektu služby SharePoint. Sloupec webu představuje typ dat, jako je například telefonní číslo, text komentáře nebo název města kontaktu v seznamu kontaktů. Další informace najdete v tématu [vytváření sloupců webu, typů obsahu a seznamů pro službu SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) a [sloupce](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Definice webu (pouze řešení farmy)
 *Definice webu* položky projektu obsahovat definice složky webu, který obsahuje následující soubory:  
  
- Výchozí stránky .aspx, použít jako výchozí webové stránky pro lokalitu.  
  
- *Onet.xml* soubor, který definuje součásti lokality.  
  
- Souboru webtemp xml, který určuje definice konfigurace serveru, které se zobrazují v **výběr šablony** část **novému Sharepointovému webu** stránky.  
  
  Po přidání definice webu, přidat kód a soubory funkci zavedou. Tuto položku projektu lze použít pouze v řešení farmy. Tuto položku projektu můžete přidat pouze řešení farmy. Další informace najdete v tématu [vytvořit definice webu pro službu SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) a [definic webu a konfigurace](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Pracovní postup stavového stroje (pouze řešení farmy)
 A *pracovní postup stavového stroje* je sada obchodní logiky stavů, přechodů a akce. Kroky v pracovní postup stavového stroje nejsou provedeny v pořadí; Místo toho se aktivují podle akcí a stavy. Podobně jako sekvenčního pracovního postupu jsou spojeny s položkami SharePoint, jako jsou seznamy a dokumenty pracovní postupy stavu počítače. Znovu můžete vytvořit pracovní postupy (globální) úrovni webu nebo seznamu úroveň (místní) pracovních postupů. Můžete také vybrat, zda pracovní postup spustí automaticky nebo ručně. Tuto položku projektu lze použít pouze v řešení farmy. Tuto položku projektu můžete přidat pouze řešení farmy. Další informace najdete v tématu [řešení pracovního postupu Sharepointu vytvořit](../sharepoint/creating-sharepoint-workflow-solutions.md), [pracovních postupů v produktu SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), a [What's New: Vylepšení pracovního postupu](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Uživatelský ovládací prvek (pouze řešení farmy)
 A *uživatelský ovládací prvek* je vlastní, opakovaně použitelné ovládací prvek, do kterého můžete přidat další ovládací prvky technologie ASP.NET a ovládací prvky služby SharePoint. Uživatelský ovládací prvek lze přidat do stránky aplikace a webové části, které běží ve službě SharePoint. Tuto položku projektu lze použít pouze v řešení farmy. Tuto položku projektu můžete přidat pouze řešení farmy. Další informace najdete v tématu [vytvoření opakovaně použitelného ovládacích prvků webové části nebo stránky aplikace](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Vizuální webové části
 A *vizuální webová část* položka projektu obsahuje *Elements.xml* soubor definice **webové části** položky a **uživatelský ovládací prvek** položky. Přetažením nebo zkopírováním ovládacích prvků na plochu uživatelského ovládacího prvku z panelu nástrojů sady Visual Studio můžete navrhnout vzhled vizuální webové části. Další informace najdete v tématu [postupy: vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) a [stavebním blokem: webové části](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Webová část
 A *webovou část* je ovládací prvek na straně serveru, který běží v rámci speciální typ stránky s názvem stránku webových částí. Jsou stavební kameny stránek, které se zobrazí na webu služby SharePoint. Položka webové části obsahuje soubory, které vám umožní navrhnout webové části webu služby SharePoint. Další informace najdete v tématu [postupy: vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) a [stavebním blokem: webové části](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Viz také:
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Produkty a technologie SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
