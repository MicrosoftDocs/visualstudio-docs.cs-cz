---
title: SharePoint projekt a šablony položek projektu | Microsoft Docs
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
ms.openlocfilehash: 825e985820ac7a4d72bf321133491e312adb0a0e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981953"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Šablony projektů a položek projektu služby SharePoint
  V následujících částech jsou popsány dostupné šablony projektu a položky projektu služby SharePoint a způsob jejich použití.

## <a name="project-and-project-item-templates-overview"></a>Přehled šablon projektů a položek projektů
 Při vytváření nového projektu služby SharePoint v aplikaci Visual Studio je projekt služby SharePoint přidán do řešení společně se všemi položkami projektu vyžadovanými tímto typem projektu. Například pokud vytvoříte projekt webové části technologie Silverlight, aplikace Visual Studio vytvoří řešení, které obsahuje položku projektu Visual Web Part a položku projektu aplikace Silverlight spolu se všemi soubory požadovanými těmito položkami projektu. Šablony položek projektu slouží k přidání položek projektu do existujícího projektu služby SharePoint, například přidání přijímače událostí, sloupce webu nebo seznamu.

 Informace o základech služby SharePoint naleznete v části [stavební bloky služby SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Pokročilí uživatelé mohou vytvořit vlastní šablony projektů a položek projektu. Další informace najdete v tématu věnovaném [roztažení systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Šablony projektů
 Následuje seznam šablon projektu služby SharePoint. Chcete-li zobrazit šablony projektu služby SharePoint v aplikaci Visual Studio, rozbalte v dialogovém okně **Nový projekt** uzel **služby SharePoint** pod položkou  **C# vizuál** nebo **Visual Basic**a pak zvolte **2010**.

### <a name="sharepoint-2010-project"></a>Projekt SharePoint 2010
 Obsah *projektu sharepoint 2010* je obsažen v každé šabloně projektu služby SharePoint. Projekt SharePoint 2010 obsahuje:

- Soubor projektu.

- Stránka vlastností projektu

- Složka **odkazuje** na seznam všech odkazů na sestavení v projektu.

- Složka **funkcí** , která obsahuje konfigurační soubor *. Feature* , který slouží k nasazení funkcí na server SharePoint.

- Složka **balíčku** , která obsahuje soubor *Package. Package* , který se používá k nasazení řešení do služby SharePoint.

- Soubor Key. snk (klíč se silným názvem), který se používá k podepsání sestavení silným názvem pro zvýšení zabezpečení.

### <a name="sharepoint-2010-silverlight-web-part"></a>Webová část SharePoint 2010 Silverlight
 Projekty *webové části služby sharepoint 2010 Silverlight* umožňují vytvořit webové části pro službu SharePoint, které zobrazují aplikace Silverlight. Při vytváření tohoto projektu můžete určit, zda se má do něj přidat nová aplikace Silverlight, nebo vytvořit odkaz na existující aplikaci. Další informace najdete v tématu [vytvoření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) a [Návod: Vytvoření webové části Silverlight, která zobrazuje OData pro službu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Visual Web SharePoint 2010 – webová část
 Projekt *Visual Web Part v SharePoint 2010* obsahuje soubor definice *Elements. XML* , položku **webové části** a položku **uživatelského ovládacího prvku** . Vzhled vizuální webové části lze navrhnout přetažením nebo zkopírováním ovládacích prvků z panelu nástrojů sady Visual Studio na plochu uživatelského ovládacího prvku. Další informace naleznete v tématu [Postupy: Vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) a [stavebního bloku: webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importovat balíček řešení pro SharePoint 2010
 *Import projektů balíčku řešení pro sharepoint 2010* umožňuje importovat všechny nebo části stávající lokality sharepointu 2010 exportované do souboru řešení služby SharePoint ( *. wsp*) do sady Visual Studio. Po importu do sady Visual Studio můžete přizpůsobit její položky a znovu je nasadit. Další informace najdete v tématu [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Import opakovaně použitelného pracovního postupu služby SharePoint 2010
 *Import opakovaně použitelných projektů pracovních postupů služby SharePoint 2010* umožňuje importovat opakovaně použitelný a deklarativní pracovní postup vytvořený v aplikaci SharePoint Designer 2010 do sady Visual Studio. Pracovní postup je exportován z webu služby SharePoint jako soubor *. wsp* . Po importu do sady Visual Studio ji můžete přizpůsobit, přidat do ní kód a pak ji nasadit na web služby SharePoint. Další informace najdete v tématu [Návod: import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Šablony položek projektu
 Následuje seznam šablon položek projektu služby SharePoint. Šablony položek projektů přidávají soubory do řešení služby SharePoint pro podporu funkcí služby SharePoint, jako jsou sloupce webu, seznamy a typy obsahu. Například přidání sloupce webu do řešení přidá sloupec webového serveru, který obsahuje soubor *. XML definice elementů* . Přidáním vizuální webové části přidáte do řešení projekt Visual Web Part, který obsahuje soubor *Elements. XML* , položku uživatelského ovládacího prvku a položku vizuální webové části.

 Chcete-li zobrazit šablony položek projektu služby SharePoint, v **Průzkumník řešení**otevřete místní nabídku projektu služby SharePoint a poté zvolte možnost **Přidat**, **Nová položka**. Rozbalte uzel **služby SharePoint** pod možností **vizuál C#**  nebo **Visual Basic**a pak zvolte **2010**.

### <a name="application-page-farm-solution-only"></a>Stránka aplikace (jenom pro řešení farmy)
 Položka **aplikace (pouze řešení farmy)** umožňuje navrhnout [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] webovou stránku pro web služby SharePoint. Stránky aplikací lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace najdete v tématu [Postup: Vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md) a [typu stránky _layouts aplikace](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Model připojení obchodních dat (jenom pro řešení farmy)
 Položka **Model připojení obchodních dat (pouze řešení farmy)** umožňuje integrovat obchodní data do služby SharePoint. Obchodní data mohou pocházet z aplikací back-end serveru, jako jsou [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel a Service Advertising Protocol (SAP). Modely připojení obchodních dat se dají použít jenom v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace najdete v tématu [Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md), [Postupy: použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)a [novinky: služby firemního připojení](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Typ obsahu
 Položky *typu obsahu* umožňují vytvářet vlastní typy obsahu založené na stávajícím typu obsahu (základní), jako je například dokument, oznámení nebo úkol. Vlastní typ obsahu poskytuje stejné atributy a pole jako základní typ obsahu spolu s libovolnými sloupci (poli) webu, které definujete. Můžete například vytvořit vlastní typ obsahu kontaktu, který je založen na základním typu obsahu kontaktu, který je součástí služby SharePoint. Typ obsahu můžete přizpůsobit tak, že změníte existující sloupce webu nebo přidáte další sloupce lokality do těch, které jsou už zahrnuté do základního typu obsahu.

> [!NOTE]
> Z důvodu omezení služby SharePoint nemůžete vytvořit typ obsahu řešení farmy na základě typu obsahu řešení v izolovaném prostoru.

 Další informace najdete v tématu [Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) a [stavebního bloku: typ obsahu](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Prázdný element
 *Prázdné prvky* se nejčastěji používají k definování položek projektu služby SharePoint, které neobsahují šablonu projektu nebo položky projektu v aplikaci Visual Studio. Přidáte-li do projektu prázdný prvek, uzel s názvem EmptyElement [x] (kde [x] je jedinečné číslo,\) je vytvořena. EmptyElement [x] obsahuje jeden soubor s názvem *Elements. XML.* Použijte příkazy [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] k definování požadovaných prvků v *Elements. XML*.

### <a name="event-receiver"></a>Přijímač událostí
 *Přijímače událostí* zpracovávají události pro položky na webu služby SharePoint, například při přidání položky do seznamu, při odstranění webové položky nebo při spuštění pracovního postupu. Šablona položky projektu příjemce události umožňuje zpracovat

- Události seznamu

- Události seznamu položek

- Vypsat události e-mailu

- Webové události

- Vypsat události pracovního postupu

  Položka projektu příjemce události vytvoří složku **přijímače událostí** s jedním souborem třídy, který obsahuje obslužné rutiny událostí pro všechny události, které jste zadali při vytváření projektu v **Průvodci vlastním nastavením služby SharePoint**. Třída přijímač událostí může zpracovávat události, ke kterým dochází na webu služby SharePoint, když se položky, jako jsou soubory, pole, položky, seznamy, přílohy, webové části a pracovní postupy, přidávají, aktualizují, odstraní nebo odeberou. Další informace najdete v tématu [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md) a [stavebního bloku: zpracování událostí](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Seznam
 Seznam je instance opakovaně použitelné definice základního SharePointového seznamu, jako je například kalendář nebo seznam úkolů. Po přidání seznamu do řešení vám Návrhář seznamu umožní přidat sloupce webu do seznamu a vytvořit vlastní sloupce seznamu. To zahrnuje sloupce webu z typů obsahu. Můžete zadat *zobrazení* seznamu, které určuje sloupce, které se zobrazí v seznamu. Další informace najdete v tématu [Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) a [stavebních bloků: seznamy a knihovny dokumentů](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Modul
 *Moduly* (Nezaměňujte pomocí [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)]ch modulů) obsahují všechny soubory, které chcete nasadit na sharepointový Server, jako jsou obrázky nebo poznámky. Položka projektu modulu obsahuje uzel **modulu** . Uzel modulu obsahuje dvě šablony položek projektu: soubor definice XML, který funguje jako manifest pro modul, a *ukázkový soubor. txt* , zástupný soubor. Další informace najdete v tématu [použití modulů k zahrnutí souborů v řešení](../sharepoint/using-modules-to-include-files-in-the-solution.md) a [modulech](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Sekvenční pracovní postup (jenom pro řešení farmy)
 *Sekvenční pracovní postup* je série kroků obchodní logiky, které se provádějí v pořadí, až do dokončení posledního kroku. Sekvenční pracovní postupy se používají ke správě procesů, které zahrnují SharePointové položky, jako jsou seznamy a dokumenty. Můžete vytvořit pracovní postupy na úrovni webu nebo pracovní postupy na úrovni seznamu (místní) a můžete vybrat, jestli se pracovní postup spustí automaticky nebo ručně. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace najdete v tématu [vytvoření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [pracovních postupů v SharePoint serveru 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))a [novinky: Vylepšení pracovního postupu](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Webová část Silverlight
 Položky projektu *webové části Silverlight* umožňují vytvořit webové části pro službu SharePoint, které zobrazují aplikace Silverlight. Když přidáte tuto položku projektu do řešení, můžete zvolit, zda chcete přidat novou aplikaci Silverlight, nebo později odkazovat na stávající. Další informace najdete v tématu [vytvoření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) a [Návod: Vytvoření webové části Silverlight, která zobrazuje OData pro službu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Sloupec webu
 *Sloupec webu*, označovaný také jako *pole*, je jedním z nejzákladnější prvků, které můžete přidat do projektu služby SharePoint. Sloupec webu představuje typ dat, jako je telefonní číslo, textový komentář nebo jméno města kontaktu v seznamu kontaktů. Další informace najdete v tématu [vytvoření sloupců webu, typů obsahu a seznamů pro službu SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) a [sloupce](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definice webu (jenom pro řešení farmy)
 Položky projektu *definice webu* obsahují složku definice webu, která obsahuje následující soubory:

- Stránka default. aspx, která slouží jako výchozí webová stránka pro daný web.

- Soubor *onet. XML* , který definuje součásti lokality.

- Soubor WebTemp XML, který určuje konfigurace definic webů, které se zobrazují v části **Výběr šablony** na **nové stránce webu SharePoint** .

  Po přidání definice webu přidáte kód a soubory, které zavádějí funkce. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace najdete v tématu [Vytvoření definic webů pro SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) a [definice a konfigurace webu](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Pracovní postup stavového stroje (jenom pro řešení farmy)
 *Pracovní postup stavového stroje* je sada stavů, přechodů a akcí obchodní logiky. Kroky v pracovním postupu stavového stroje nejsou prováděny v sekvenci. místo toho jsou aktivovány akcemi a stavy. Podobně jako sekvenční pracovní postup jsou pracovní postupy stavového stroje přidruženy k položkám SharePointu, jako jsou seznamy a dokumenty. Znovu můžete vytvořit pracovní postupy na úrovni webu nebo pracovní postupy na úrovni seznamu (místní). Můžete také vybrat, jestli se má pracovní postup spustit automaticky nebo ručně. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace najdete v tématu [vytvoření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [pracovních postupů v SharePoint serveru 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))a [novinky: Vylepšení pracovního postupu](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Uživatelský ovládací prvek (pouze pro řešení farmy)
 *Uživatelský ovládací prvek* je vlastní, opakovaně použitelný ovládací prvek, do kterého můžete přidat další ovládací prvky ASP.NET a SharePoint. Uživatelský ovládací prvek lze přidat na stránky aplikace a webové části, které jsou spuštěny v rámci služby SharePoint. Tuto položku projektu lze použít pouze v řešeních farmy. Tuto položku projektu můžete přidat pouze do řešení farmy. Další informace naleznete v tématu [vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](/visualstudio/sharepoint/creating-reusable-controls-for-web-parts-or-application-pages&view=vs-2019).

### <a name="visual-web-part"></a>Vizuální webová část
 Položka projektu *vizuální webové části* obsahuje soubor definice *Elements. XML* , položku **webové části** a položku **uživatelského ovládacího prvku** . Vzhled vizuální webové části lze navrhnout přetažením nebo zkopírováním ovládacích prvků z panelu nástrojů sady Visual Studio na plochu uživatelského ovládacího prvku. Další informace naleznete v tématu [Postupy: Vytvoření webové části služby SharePoint pomocí návrháře](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) a [stavebního bloku: webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Webová část
 *Webová část* je ovládací prvek na straně serveru, který běží uvnitř speciálního typu stránky s názvem stránka webové části. Jsou to stavební kameny stránek, které se zobrazují na webu služby SharePoint. Položka webové části poskytuje soubory, které umožňují návrh webové části pro web služby SharePoint. Další informace naleznete v tématu [Postupy: Vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) a [stavebního bloku: webové části](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Viz také:
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Produkty a technologie pro SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
