---
title: Šablony sharepointového projektu a položek projektu | Dokumenty společnosti Microsoft
ms.date: 02/22/2017
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
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649228"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Šablony sharepointových projektů a položek projektu
  Následující části popisují dostupné šablony sharepointového projektu a položek projektu a způsob jejich použití.

## <a name="project-and-project-item-templates-overview"></a>Přehled šablon položek projektu a projektu
 Při vytváření nového sharepointového projektu v sadě Visual Studio se do řešení přidá sharepointový projekt spolu se všemi položkami projektu vyžadovanými daným typem projektu. Pokud například vytvoříte projekt webové části Silverlight, visual studio vytvoří řešení, které obsahuje položku projektu webové části Visual Web A položku projektu aplikace Silverlight spolu se všemi soubory vyžadované těmito položkami projektu. Šablony položek projektu se používají k přidání položek projektu do existujícího sharepointového projektu, jako je například přidání příjemce události, sloupce webu nebo seznamu.

 Informace o základech SharePointu najdete v [tématu Stavební bloky SharePoint foundation .](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)) Pokročilí uživatelé mohou vytvářet vlastní šablony položek projektu a projektu. Další informace naleznete [v tématu Rozšíření systému projektů služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Šablony projektů
 Následuje seznam šablon projektů sharepointového projektu. Pokud chcete zobrazit šablony sharepointového projektu v Sadě Visual Studio, rozbalte v dialogovém okně **Nový projekt** uzel **SharePoint** u **Visual C#** nebo **Visual Basic**a pak zvolte **2010**.

### <a name="sharepoint-2010-project"></a>Projekt SharePointu 2010
 Obsah *SharePointu 2010 Projectu* je součástí každé šablony sharepointového projektu. SharePoint 2010 Project obsahuje:

- Soubor projektu.

- Stránka vlastností projektu.

- A **Reference složka** seznam všech odkazů na sestavení v projektu.

- Složka **Funkce,** která obsahuje konfigurační soubor *.feature,* který se používá k nasazení funkcí na sharepointový server.

- Složka **Package,** která obsahuje soubor *Package.package,* který slouží k nasazení řešení na SharePoint.

- Soubor key.snk (klíč silného názvu), který se používá k podepsání sestavení silným názvem pro rozšířené zabezpečení.

### <a name="sharepoint-2010-silverlight-web-part"></a>Webová část SharePoint 2010 Silverlight
 *Projekty webových částí Silverlight sharepointu 2010* umožňují vytvářet webové části pro SharePoint, které zobrazují aplikace Silverlight. Při vytváření tohoto projektu můžete určit, zda do něj chcete přidat novou aplikaci Silverlight nebo odkazovat na existující aplikaci. Další informace najdete [v tématu Vytvoření webových částí pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) a [Návod: Vytvoření webové části Silverlight, která zobrazuje OData pro SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Vizuální webová část SharePointu 2010
 Projekt *webové části Visual SharePoint 2010* obsahuje definiční soubor *Elements.xml,* položku **webové části** a položku **Uživatelského ovládacího prvku.** Vzhled vizuální webové části můžete navrhnout přetažením nebo zkopírováním ovládacích prvků z panelu nástrojů sady Visual Studio na povrch uživatelského ovládacího prvku. Další informace najdete v [tématu Postup: Vytvoření webové části SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) a [stavebního bloku: Webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Import balíčku řešení SharePointu 2010
 *Import projektů balíčků řešení SharePointu 2010* umožňuje importovat celý existující web SharePointu 2010 nebo jeho část exportovaný do sharepointového řešení *(WSP)* do Sady Visual Studio. Po importu do sady Visual Studio můžete přizpůsobit jeho položky a znovu je nasadit. Další informace naleznete [v tématu Import položek z existujícího sharepointového webu](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Import opakovaně použitelného pracovního postupu SharePointu 2010
 Importujte opakovaně použitelné projekty *pracovního postupu SharePointu 2010* umožňují importovat opakovaně použitelný deklarativní pracovní postup vytvořený v SharePoint Designeru 2010 do Sady Visual Studio. Pracovní postup se exportuje z webu služby SharePoint jako soubor *WSP.* Po importu do sady Visual Studio ho můžete přizpůsobit, přidat do něj kód a pak ho nasadit na sharepointový web. Další informace naleznete [v tématu Návod: Import opakovaně použitelného pracovního postupu SharePoint Designeru do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Šablony položek projektu
 Následuje seznam šablon položek projektu SharePointu. Šablony položek projektu přidávají soubory do řešení SharePointu, aby podporovaly funkce SharePointu, jako jsou sloupce webu, seznamy a typy obsahu. Například přidání sloupce webu do vašeho řešení přidá projekt sloupce webu, který obsahuje definiční soubor *Elements.xml.* Přidání vizuální webové části přidá do vašeho řešení projekt vizuální webové části, který obsahuje soubor *Elements.xml,* položku uživatelského ovládacího prvku a vizuální položku webové části.

 Pokud chcete zobrazit šablony položek projektu SharePointu, otevřete v **Průzkumníku řešení**místní nabídku pro sharepointový projekt a pak zvolte **Přidat**, **Nová položka**. Rozbalte uzel **SharePoint** v části **Visual C#** nebo **Visual Basic**a pak zvolte **2010**.

### <a name="application-page-farm-solution-only"></a>Stránka aplikace (pouze řešení farmy)
 Položka **Stránka aplikace (pouze farma_ řešení)** umožňuje navrhnout webovou stránku [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pro sharepointový web. Stránky aplikací lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace naleznete v [tématu How to: Create an application page](../sharepoint/how-to-create-an-application-page.md) and Application _layouts Page [Type](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Model připojení obchodních dat (pouze řešení farmy)
 Položka **modelu připojení obchodních dat (pouze farmové řešení)** umožňuje integrovat obchodní data do SharePointu. Obchodní data mohou pocházet z aplikací [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]back-end serveru, jako je například , Siebel a Service Advertising Protocol (SAP). Modely připojení obchodních dat lze použít pouze v zemědělských řešeních. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace naleznete v [tématech Postup: Vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md), [Postup: Použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)a [Co je nového: Služba podnikového připojení](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Typ obsahu
 Položky *typu obsahu* umožňují vytvářet vlastní typy obsahu na základě existujícího (základního) typu obsahu, jako je dokument, oznámení nebo úkol. Vlastní typ obsahu poskytuje stejné atributy a pole jako základní typ obsahu spolu se všemi sloupci webu (poli), které definujete. Můžete například vytvořit vlastní typ obsahu kontaktu, který je založen na základním typu obsahu kontaktu, který je dodáván v SharePointu. Typ obsahu můžete přizpůsobit změnou existujících sloupců webu nebo přidáním dalších sloupců webu k sloupcům, které jsou již zahrnuty v základním typu obsahu.

> [!NOTE]
> Z důvodu omezení služby SharePoint nelze vytvořit typ obsahu řešení farmy založený na typu obsahu řešení v izolovaném prostoru.

 Další informace [najdete v tématu Návod: Vytvoření sloupce webu, typu obsahu a seznamu pro SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) a [Stavební blok: Typ obsahu](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Prázdný prvek
 *Prázdné prvky* se nejčastěji používají k definování položek projektu sharepointového projektu, které v sadě Visual Studio postrádají šablonu projektu nebo položky projektu. Přidáte-li do projektu prázdný prvek, vytvoří se uzel s názvem EmptyElement[x](kde [x] je jedinečné číslo.\) EmptyElement[x] obsahuje jeden soubor s názvem *Elements.xml.* Příkazy slouží [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] k definování požadovaných prvků v *souboru Elements.xml*.

### <a name="event-receiver"></a>Přijímač událostí
 *Příjemci událostí* zpracovávají události pro položky na sharepointovém webu, například když je položka přidána do seznamu, když je webová položka odstraněna nebo když je spuštěn pracovní postup. Šablona položky projektu příjemce události umožňuje zpracovat

- Seznam událostí

- Události položky seznamu

- Seznam e-mailových událostí

- Webové události

- Seznam událostí pracovního postupu

  Položka projektu příjemce události vytvoří složku **příjemce události** s jedním souborem třídy, který obsahuje obslužné rutiny událostí pro všechny události, které jste zadali při vytváření projektu v **Průvodci vlastním nastavením služby SharePoint**. Třída příjemce události dokáže zpracovat události, ke kterým dochází na webu služby SharePoint, když jsou přidány, aktualizovány, odstraněny nebo odebrány položky, jako jsou soubory, pole, položky, seznamy, přílohy, webové části a pracovní postupy. Další informace naleznete v [tématu How to: Create a event receiver](../sharepoint/how-to-create-an-event-receiver.md) and Building [Block: Event Handling](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Seznam
 Seznam je instancí třídy definice seznamu opakovaně použitelné ho služby SharePoint, například kalendáře nebo seznamu úkolů. Po přidání seznamu do vašeho řešení umožňuje Návrhář seznamu přidávat do seznamu sloupce webu a vytvářet vlastní sloupce seznamu. To zahrnuje sloupce webu z typů obsahu. Můžete určit *zobrazení* seznamu, které určuje sloupce, které se zobrazí v seznamu. Další informace [najdete v tématu Návod: Vytvoření sloupce webu, typu obsahu a seznamu pro SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) a [stavební blok: Seznamy a knihovny dokumentů](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Modul
 *Moduly* (nezaměňovat [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] s moduly) obsahují všechny soubory, které chcete nasadit na sharepointový server, například obrázky nebo poznámky. Položka projektu modulu obsahuje uzel **modulu.** Uzel modulu obsahuje dvě šablony položek projektu: definiční soubor XML, který slouží jako manifest pro modul, a soubor *sample.txt,* zástupný soubor. Další informace naleznete [v tématu Použití modulů k zahrnutí souborů do řešení](../sharepoint/using-modules-to-include-files-in-the-solution.md) a [modulů](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Sekvenční pracovní postup (pouze řešení farmy)
 *Sekvenční pracovní postup* je řada kroků obchodní logiky prováděných postupně až do dokončení posledního kroku. Sekvenční pracovní postupy se používají ke správě procesů, které zahrnují položky služby SharePoint, jako jsou seznamy a dokumenty. Můžete vytvořit pracovní postupy na úrovni webu (globální) nebo pracovní postupy na úrovni seznamu (místní) a můžete vybrat, zda se pracovní postup spustí automaticky nebo ručně. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace najdete [v tématech Vytvoření řešení pracovních postupů služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [Pracovní postupy na SharePoint Serveru 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))a [Co je nového: Vylepšení pracovního postupu](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Webová část Silverlight
 *Položky* projektu webové části Silverlight umožňují vytvářet webové části pro SharePoint, které zobrazují aplikace Silverlight. Když přidáte tuto položku projektu do vašeho řešení, můžete zvolit, zda chcete přidat novou aplikaci Silverlight nebo odkazovat na existující aplikaci později. Další informace najdete [v tématu Vytvoření webových částí pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) a [Návod: Vytvoření webové části Silverlight, která zobrazuje OData pro SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Sloupec Pracoviště
 *Sloupec webu*, označovaný také jako *pole*, je jedním z nejzákladnějších prvků, které lze přidat do sharepointového projektu. Sloupec webu představuje typ dat, například telefonní číslo, textový komentář nebo název města kontaktu v seznamu kontaktů. Další informace najdete [v tématu Vytváření sloupců webu, typů obsahu a seznamů pro SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) a [sloupce](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definice lokality (pouze řešení farmy)
 Položky *projektu definice webu* obsahují složku definice webu, která obsahuje následující soubory:

- Výchozí stránka ASPX použitá jako výchozí webová stránka webu.

- Soubor *onet.xml,* který definuje součásti webu.

- Soubor XML webtemp, který určuje konfigurace definice webu, které se zobrazí v části **Výběr šablony** na stránce **Nový web služby SharePoint.**

  Po přidání definice webu přidáte kód a soubory, které zavedou funkce. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace naleznete v [tématu Vytváření definic webů pro SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) a [definice a konfigurace webu](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Pracovní postup stavového počítače (pouze řešení farmy)
 *Pracovní postup stavového počítače* je sada stavů obchodní logiky, přechodů a akcí. Kroky v pracovním postupu stavového počítače nejsou prováděny postupně; místo toho jsou spouštěny akcemi a státy. Pracovní postupy stavového počítače jsou podobně jako sekvenční pracovní postupy přidruženy k položkám služby SharePoint, jako jsou seznamy a dokumenty. Znovu můžete vytvářet pracovní postupy na úrovni webu (globální) nebo pracovní postupy na úrovni seznamu (místní). Můžete také vybrat, zda se pracovní postup spustí automaticky nebo ručně. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace najdete [v tématech Vytvoření řešení pracovních postupů služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [Pracovní postupy na SharePoint Serveru 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))a [Co je nového: Vylepšení pracovního postupu](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Uživatelské řízení (pouze řešení farmy)
 *Uživatelský ovládací prvek* je vlastní opakovaně použitelný ovládací prvek, do kterého můžete přidat další ovládací prvky ASP.NET a ovládací prvky služby SharePoint. Uživatelský ovládací prvek lze přidat do stránek aplikace a webových částí, které běží v SharePointu. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace naleznete [v tématu Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Vizuální webová část
 Položka projektu *vizuální webové části* obsahuje definiční soubor *Elements.xml,* položku **webové části** a položku **Uživatelského ovládacího prvku.** Vzhled vizuální webové části můžete navrhnout přetažením nebo zkopírováním ovládacích prvků z panelu nástrojů sady Visual Studio na povrch uživatelského ovládacího prvku. Další informace najdete v [tématu Postup: Vytvoření webové části SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) a [stavebního bloku: Webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Webová část
 *Webová část* je ovládací prvek na straně serveru, který běží uvnitř speciálního typu stránky nazývané stránka webových částí. Jedná se o stavební kameny stránek, které se zobrazují na sharepointovém webu. Položka webové části obsahuje soubory, které umožňují navrhnout webovou část pro sharepointový web. Další informace najdete v [tématu Postup: Vytvoření webové části SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) a [Stavební blok: Webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Viz také
- [Vývoj řešení SharePointu](../sharepoint/developing-sharepoint-solutions.md)
- [Produkty a technologie Služby SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
