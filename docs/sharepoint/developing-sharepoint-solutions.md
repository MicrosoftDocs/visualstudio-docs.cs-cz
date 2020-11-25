---
title: Vývoj řešení služby SharePoint | Microsoft Docs
description: Vývoj řešení služby SharePoint. Znáte prvky projektu služby SharePoint. Pochopení projektu SharePoint a vlastností položek projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 755723dd2ae309e971e86852646ee33d2caa22cf
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970394"
---
# <a name="develop-sharepoint-solutions"></a>Vývoj řešení služby SharePoint
  V nástroji je k dispozici několik šablon typu projektu služby SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pro vytváření webů a prvků webu služby SharePoint. Seznam dostupných typů projektů naleznete v tématu [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md). Následuje popis prvků a vlastností projektu služby SharePoint.

 Informace o SharePoint 2013 a doplňkůch pro SharePoint najdete v tématu [sharepoint 2013](https://www.microsoft.com/microsoft-365/previous-versions/microsoft-sharepoint-2013) a [sestavení doplňků pro SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

## <a name="elements-of-a-sharepoint-project"></a>Prvky projektu služby SharePoint
 Uzly v rámci projektu služby SharePoint jsou označovány jako *položky služby SharePoint*. Položky SharePointu mohou obsahovat také jeden nebo více podsouborů, označovaných jako *soubory položek služby SharePoint*, například [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] konfigurační soubory, formuláře. aspx a další.

 Namísto vytváření projektů pomocí šablon projektu, které jsou již naplněny soubory položek projektu, můžete použít prázdnou šablonu **projektu** k vytvoření prázdného projektu služby SharePoint a poté přidat položky projektu ručně. Projekty SharePoint mohou také volitelně obsahovat jeden nebo více souborů funkcí (pro aktivaci v SharePointu) a soubor balíčku, ve kterém chcete projekt distribuovat.

### <a name="special-nodes"></a>Speciální uzly
 Každý projekt služby SharePoint obsahuje dva uzly, které nemohou být přejmenovány, odstraněny, vyjmuty, zkopírovány nebo přetaženy z projektu. Tyto uzly jsou následující:

- Funkce
- Balíček

  Oba uzly se vždy zobrazí ve všech projektech SharePoint i v případě, že pro projekt nejsou definovány žádné funkce nebo balíčky.

#### <a name="features-node"></a>Uzel funkcí
 Uzel **funkcí** obsahuje jednu nebo více funkcí projektu služby SharePoint. Funkce je kontejner rozšíření pro službu SharePoint. Po nasazení funkce na SharePoint Server ji můžete zahrnout do definic webů nebo je aktivovat jednotlivě pomocí Správce služby SharePoint na webech SharePoint. Další informace najdete v tématu [práce s funkcemi](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

 Pokud přidáte položku, například typ obsahu nebo instanci seznamu, do projektu služby SharePoint, je přidána do funkce v uzlu **funkce** . Rozsah položky určuje, zda je přidána do nové nebo existující funkce. Pokud má nová položka stejný obor jako stávající funkce, přidá se do této funkce. V opačném případě se položka přidá do nové funkce.

 Chcete-li ručně přidat funkci, spusťte příkaz **Přidat funkci** v místní nabídce uzlu funkce. Obsah funkce můžete zobrazit nebo změnit pomocí návrháře funkcí. Další informace naleznete v tématu [How to: Customize a SharePoint Feature](../sharepoint/how-to-customize-a-sharepoint-feature.md).

 Při přidání funkce do projektu služby SharePoint se zobrazí v **Průzkumník řešení** jako uzel s výchozí funkcí name *x*. Feature, kde *x* je jedinečné číslo. Po nasazení funkce na server SharePoint může ji správce služby SharePoint aktivovat a zpřístupnit ji uživatelům webu služby SharePoint.

#### <a name="package-node"></a>Uzel balíčku
 Uzel **balíčku** obsahuje jeden soubor, který slouží jako mechanismus distribuce pro projekt služby SharePoint. Tento soubor, známý jako *balíček řešení*, je. CAB založený na. Rozšíření WSP Balíček řešení je nasaditelné, opakovaně použitelný soubor, který obsahuje sadu funkcí, definic webů a sestavení, které se vztahují na weby SharePointu a které můžete povolit nebo zakázat jednotlivě. Uzel **balíčku** také vždy obsahuje soubor s názvem Package. wspdef, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] definiční soubor balíčku. Po nasazení balíčku na server, na kterém je spuštěna služba SharePoint, může správce služby SharePoint nainstalovat a aktivovat jeho funkce.

 Můžete zobrazit nebo změnit obsah balíčku v Návrháři balíčku Poklikáním na uzel balíčku nebo otevřením jeho místní nabídky a následným výběrem možnosti **otevřít**. Další informace najdete v tématu [vytváření balíčků řešení služby SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

## <a name="sharepoint-project-and-project-item-properties"></a>Vlastnosti projektu a položky projektu služby SharePoint
 Projekty služby SharePoint, stejně jako jiné [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty, zobrazují vlastnosti na okno Vlastnosti a na stránce vlastností. Vlastnosti, které jsou zobrazeny, závisí na uzlu, který je vybrán.

 Když je v **Průzkumník řešení** vybrán projekt služby SharePoint, položka projektu nebo soubor položky projektu, v okno Vlastnosti nebo na stránce vlastností se zobrazí následující vlastnosti:

### <a name="project-properties"></a>Vlastnosti projektu

|Název vlastnosti|Description|
|-------------------|-----------------|
|Konfigurace aktivního nasazení|Určuje řadu kroků provedených během nasazování. Další informace najdete v tématu [Postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Cíl nasazení sestavení|Určuje, kde se nachází *sestavení aplikace služby SharePoint* . Platné hodnoty umístění sestavení jsou buď *GlobalAssemblyCache* (výchozí), nebo *WebApplication*.<br /><br /> Pokud je vlastnost *řešení v izolovaném prostoru* nastavena na **hodnotu true**, tato vlastnost je zakázána.|
|Automatické odvolání po ladění|Určuje, zda se nasazené řešení po spuštění aplikace v režimu ladění v nástroji automaticky odvolá ze služby SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Je-li vybrána tato možnost, řešení se odvolá, když se IDE po ladění vrátí zpět do návrhového zobrazení. Pokud je zaškrtnuto, řešení se neodvolává. Další informace najdete v tématu [odvolání řešení](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14)).|
|Upravit konfigurace|Určuje konfiguraci nasazení, která se má použít pro projekt. Další informace najdete v tématu [Postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) a [nasazení, publikování a Upgrade balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|
|Povolit ladění Silverlight (místo ladění skriptu)|Je-li vybrána tato možnost, ladicí program Silverlight se připojí k procesu ladění. Pokud je zaškrtnuto, ladicí program skriptu se připojí k procesu ladění. Další informace najdete v tématu [Přehled ladění Silverlight](/previous-versions/windows/).|
|Zahrnout sestavení do balíčku|Určuje, zda je sestavení projektu zabaleno v čase sestavení, nebo ne.|
|Příkazový řádek po nasazení|Určuje příkazy, které se mají spustit po nasazení řešení služby SharePoint. Tento řádek podporuje jakékoli dávkové příkazy a také rozlišení proměnných MSBuild. Další informace najdete v tématu [Postup: nastavení příkazů nasazení služby SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Příkazový řádek před nasazením|Určuje příkazy, které mají být spuštěny před nasazením řešení služby SharePoint. Tento řádek podporuje jakékoli dávkové příkazy a také rozlišení proměnných MSBuild. Další informace najdete v tématu [Postup: nastavení příkazů nasazení služby SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Soubor projektu|Název souboru, který obsahuje sestavení, konfiguraci a další informace o projektu.|
|Složka projektu|Umístění souboru projektu v systému. (Jen pro čtení.)|
|Řešení v izolovaném prostoru|Určuje, jestli se má projekt nasadit jako *řešení v izolovaném prostoru*, označované také jako *řešení vytvořené uživatelem*. Řešení v izolovaném prostoru nejsou nutně důvěryhodná. Hodnota **true** znamená, že projekt je nasazen jako řešení v izolovaném prostoru, hodnota **false** znamená, že projekt je nasazen jako řešení farmy. Další informace najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md) a [rozdíly mezi řešeními v izolovaném prostoru a řešeních farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|Adresa URL webu|Určuje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] cílovou lokalitu pro tento projekt.|
|Spouštěcí položka|Určuje první položku v projektu, která se má spustit.|

 Když vyberete soubor položky služby SharePoint (například pracovní postup nebo funkce v uzlu funkce), zobrazí se v okno Vlastnosti následující vlastnosti:

### <a name="project-item-properties"></a>Vlastnosti položky projektu

|Název vlastnosti|Description|
|-------------------|-----------------|
|Řešení konfliktů při nasazení|Určuje akci, která má být provedena při nasazení položky projektu, jejíž vlastnosti jsou stejné jako u položky, která je již na serveru. Další informace najdete v tématu [řešení potíží s balíčkem a nasazením služby SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|
|Vlastnosti funkce|Určuje sadu hodnot (uložených jako páry klíč/hodnota), která je součástí funkce při nasazení do služby SharePoint. Po nasazení funkce můžete získat přístup k hodnotám vlastností v kódu. Další informace naleznete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Přijímač funkcí|Poskytuje kód, který se spustí, když dojde k určitým událostem obsahujícím funkci položky projektu. Další informace naleznete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Název složky|Název složky položky projektu služby SharePoint.|
|Odkazy na výstup projektu|Určuje závislost, jako je například sestavení, kterou musí vaše položka projektu spustit. Další informace naleznete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Položky bezpečného řízení|Určuje ovládací prvky, které jsou bezpečné pro nedůvěryhodné uživatele k úpravám. Další informace naleznete v tématu [poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Vlastnosti souboru položky projektu

|Název vlastnosti|Description|
|-------------------|-----------------|
|Akce sestavení|Určuje, jak se soubor vztahuje k procesům sestavení a nasazení. Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Kopírovat do výstupního adresáře|Určuje, zda budou zdrojové soubory zkopírovány do výstupního adresáře. Může to být jedna z následujících hodnot:<br /><br /> -   *Nekopírovat*<br />-   *Vždycky kopírovat*<br />-   *Kopírovat, pokud je novější*<br /><br /> Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Vlastní nástroj|Určuje název nástroje (pokud existuje), který transformuje soubor v době návrhu a umístí výstup transformace do jiného souboru. Například soubor datové sady (. [!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)] ) má výchozí vlastní nástroj. Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Obor názvů vlastního nástroje|Obor názvů, do kterého se kopíruje výstup vlastního nástroje. Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Umístění nasazení|Plně kvalifikovaná cesta k souboru na serveru SharePoint. Tato cesta se skládá z kořene nasazení a cesty nasazení podvlastností.|
|Cesta nasazení|Relativní cesta k souboru v souboru serveru SharePoint, například Workflow1 \\ . Plně kvalifikovaná cesta k souboru je vytvořena zřetězením hodnoty *cesty nasazení* na konec *kořenové hodnoty nasazení* .<br /><br /> Výběr hodnoty *RootFile* pro vlastnost *typ nasazení* změní *kořenovou vlastnost nasazení* na \<SharePointRoot> \\ . Výsledkem je plně kvalifikovaná cesta \<SharePointRoot> \Workflow1 \\ . Další informace naleznete v tématu [balení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Kořen nasazení|Řetězec. Kořenová složka, ve které je soubor nasazen na serveru SharePoint. Například \<SharePointRoot> \Template\Features \\ \<FeatureName> \\ .<br /><br /> Hodnota *kořenové vlastnosti nasazení* je určena nastavením *typ nasazení* .|
|Typ nasazení|Typ nasazení souboru, který určuje jeho *kořenovou hodnotu nasazení* . Může to být jedna z následujících hodnot:<br /><br /> Nasazení: *\<no value>*<br /><br /> ElementManifest: *\<SharePointRoot> \Template\Features \\ \<FeatureName>*\\<br /><br /> ElementFile: *\<SharePointRoot> \\ \<FeatureName> \Template\Features \\*<br /><br /> TemplateFile: *\<SharePointRoot> \TEMPLATE \\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot> \Resources \\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Další informace naleznete v tématu <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Název souboru|Název souboru nebo složky pro soubor položky|
|Úplná cesta|Umístění souboru pro položku (Jen pro čtení.)|

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Šablony projektů a položek projektů služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)|Popisuje projekt služby SharePoint a šablony položek projektu, které jsou k dispozici v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Postupy: Přidání položek do projektu služby SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Popisuje, jak přidat nové nebo existující položky do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.|
|[Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Provede vás krok za krokem vytvoření pole zákazníka, typu obsahu, definice seznamu a instance seznamu.|
|[Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)|Popisuje postup přidání přijímače událostí pro projekt vytvořený v [návodu: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|
|[Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Popisuje, jak vytvořit projekty pracovního postupu, které zahrnují formuláře přidružení pracovního postupu a inicializační formuláře pracovního postupu.|
|[Vytváření stránek pro SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Popisuje, jak můžete vytvářet stránky, například stránky aplikace, stránky webu, stránky předlohy a rozložení stránek pro službu SharePoint.|
|[Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Popisuje, jak přidat ovládací prvky, které uživatelům umožňují přímo upravit obsah, vzhled a chování stránek webu služby SharePoint pomocí prohlížeče.|
|[Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Popisuje, jak vytvořit uživatelské ovládací prvky, které mohou být spotřebovány stránkami aplikace a Webové části, které běží na SharePointu.|
|[Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Popisuje, jak integrovat data z webových služeb a back-endové aplikace serveru do aplikace služby SharePoint.|
|[Vytvořit definice webu pro SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Popisuje, jak vytvořit definice webu: šablony používané k vytvoření webů SharePointu.|
|[Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Popisuje, jak importovat položky, jako jsou typy obsahu a moduly z existujícího webu služby SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.|
|[Vložení souborů do řešení pomocí modulů](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Popisuje, jak použít moduly k nasazení souborů z vašeho [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu na web služby SharePoint.|
|[Procházení připojení služby SharePoint pomocí Průzkumník serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Popisuje postup procházení místních webů služby SharePoint pomocí Průzkumník serveru.|
|[Poskytnutí informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Popisuje, jak použít vlastnosti položek projektu k poskytnutí informací o balení a nasazení pro projekty, jako jsou položky bezpečného řízení, odkazy na výstup projektu a vlastnosti funkce.|
|[Postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Popisuje, jak lze do projektu přidat mapované složky, které poskytují snazší přístup k prostředkům služby SharePoint.|
|[Otázky řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md)|Popisuje problémy spojené s řešeními v izolovaném prostoru.|
|[Zabezpečení pro řešení služby SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Popisuje bezpečnostní opatření pro vývoj řešení služby SharePoint v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Dialogové okno pro výběr adresy URL &#40;vývoj pro SharePoint v aplikaci Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Popisuje dialogové okno, které lze použít k přidání odkazů na prostředky v projektu nebo na místním serveru SharePoint.|

## <a name="see-also"></a>Viz také
- [Začínáme &#40;vývoj pro SharePoint v aplikaci Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Procházení připojení služby SharePoint pomocí Průzkumník serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
