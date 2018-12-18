---
title: Vývoj řešení služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25a7402a8d0464152e9b1bdd9d2edcdc66824914
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295901"
---
# <a name="develop-sharepoint-solutions"></a>Vývoj řešení služby SharePoint
  Několik šablon typu projektu služby SharePoint jsou k dispozici v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pro vytváření webů služby SharePoint a prvků na webu. Seznam dostupných typů projektu naleznete v tématu [SharePoint šablony položek projektu a projekt](../sharepoint/sharepoint-project-and-project-item-templates.md). Následuje popis prvků a vlastností projektu služby SharePoint.  
  
 Informace o SharePoint 2013 a doplňky pro SharePoint, naleznete v tématu [SharePoint 2013](https://msdn.microsoft.com/library/jj162979.aspx) a [vytváření Sharepointových doplňků](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).  
  
## <a name="elements-of-a-sharepoint-project"></a>Prvky projektu služby SharePoint
 Uzly v rámci projektu služby SharePoint jsou označovány jako *položek Sharepointového*. Položky služby SharePoint mohou obsahovat také jeden nebo více podsouborů, označované jako *soubory položek Sharepointového*, jako například [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] konfigurační soubory, formuláře .aspx a další.  
  
 Namísto vytváření projektů pomocí šablon projektů, které jsou již předvyplněny soubory s položkami projektu, můžete použít **prázdný projekt** šablony vytvořit prázdný projekt SharePoint a potom ručně přidat položky projektu. Projekty SharePoint mohou volitelně obsahovat také jeden nebo více souborů funkcí (pro aktivaci ve službě SharePoint) a soubor balíčku pro distribuci projektu.  
  
### <a name="special-nodes"></a>Speciální uzly
 Každý projekt služby SharePoint obsahuje dva uzly, které nelze přejmenovat, odstranit, Vyjmout, kopírovat nebo přetáhnout z projektu. Tyto uzly jsou následující:  
  
- Funkce    
- Balíček  
  
  Oba uzly se vždy zobrazí ve všech projektech SharePoint i v případě, že žádné funkce nebo balíčky nejsou definovány pro projekt.  
  
#### <a name="features-node"></a>Uzel funkcí
 **Funkce** uzel obsahuje jeden nebo více funkcí projektu SharePoint. Funkce je kontejner rozšíření pro službu SharePoint. Po nasazení funkce na SharePoint server může být zahrnuta do definic webu nebo aktivována jednotlivě správci služby SharePoint na webech služby SharePoint. Další informace najdete v tématu [práce s funkcemi](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Při přidání položky, jako je například typ obsahu nebo instance seznamu do projektu služby SharePoint, přidá se do funkce **funkce** uzlu. Rozsah položky určuje, zda je přidána do existující nebo nové funkce. Pokud je nová položka stejném oboru jako stávající funkce, je přidána do této funkce. V opačném případě je položka přidána do nové funkce.  
  
 Pokud chcete ručně přidat funkci, spusťte **přidat funkci** příkazu v místní nabídce zkratky uzlu funkce. Můžete zobrazit nebo změnit obsah funkce pomocí návrháře funkcí. Další informace najdete v tématu [postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Pokud funkce je přidána do projektu služby SharePoint, zobrazí se v **Průzkumníka řešení** jako uzel s výchozím názvem funkce*x*.feature, kde *x* je jedinečné číslo. Po nasazení funkce k Sharepointovému serveru, správce Sharepointu si ji můžou aktivovat, jejich zpřístupnění uživatelům webu služby SharePoint.  
  
#### <a name="package-node"></a>Uzel balíčku
 **Balíčku** uzel obsahuje jeden soubor, který slouží jako mechanismus rozdělení projektu služby SharePoint. Tento soubor, známý jako *balíčku řešení*, je. Na základě souboru CAB se. Rozšíření WSP. Balíček řešení je nasaditelný, opakovaně použitelný soubor, který obsahuje sadu funkcí, definic webu a sestavení, které se týkají weby služby SharePoint a že můžete povolit nebo zakázat jednotlivě. **Balíčku** uzel také vždy obsahuje soubor s názvem Package.wspdef, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] definiční soubor balíčku. Po nasazení balíčku na serveru, na kterém je spuštěna služba SharePoint, Správce služby SharePoint, můžete jej nainstalovat a aktivovat její funkce.  
  
 Můžete zobrazit nebo změnit obsah balíčku v Návrháři balíčku poklepáním na uzel balíčku nebo otevřením jeho místní nabídku a následným výběrem možnosti **otevřít**. Další informace najdete v tématu [balíčků řešení služby SharePoint vytvořit](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>A vlastnosti položky projektu služby SharePoint
 Projekty SharePoint, stejně jako ostatní [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty, zobrazit vlastnosti v okně vlastností a stránky vlastností. Vlastnosti, které jsou zobrazeny, závisí na uzlu, který je vybrán.  
  
 Když je projekt SharePoint, položku projektu nebo soubor položky uzlu je vybrána v **Průzkumníka řešení**, následující vlastnosti se zobrazí v okně vlastností nebo na stránce vlastností:  
  
### <a name="project-properties"></a>Vlastnosti projektu
  
|Název vlastnosti|Popis|  
|-------------------|-----------------|  
|Aktivní konfigurace nasazení|Určuje řadu kroků prováděných během nasazování. Další informace najdete v tématu [postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Cíl nasazení sestavení|Určí, kde *sestavení aplikace SharePoint* nacházejí. Platné hodnoty umístění sestavení jsou buď *GlobalAssemblyCache* (výchozí), nebo *WebApplication*.<br /><br /> Pokud *řešení v izolovaném prostoru* je nastavena na **true**, pak tato vlastnost deaktivována.|  
|Automatické odvolání po ladění|Určuje, jestli řešení nasazení automaticky odvolá ze serveru SharePoint po spuštění aplikace v režimu ladění v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Při výběru řešení odvolání při IDE přejde zpět do návrhového zobrazení po ladění. Není-li zaškrtnuto, není odvolat řešení. Další informace najdete v tématu [stahování řešení](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Upravit konfigurace|Určuje konfiguraci nasazení pro projekt. Další informace najdete v tématu [postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) a [nasazení, publikování a upgradování balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Povolit ladění Silverlight (místo ladění skripty)|Pokud je vybráno, připojí se Silverlight debugger k ladění procesu. Není-li zaškrtnuto, připojí Script debugger k ladění procesu. Další informace najdete v tématu [Přehled ladění Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Zahrnout sestavení v balíčku|Určuje, zda je sestavení projektu zabalit v okamžiku sestavení, nebo ne.|  
|Příkazový řádek po nasazení|Určuje, které příkazy se spustí po nasazení řešení služby SharePoint. Tento řádek podporuje libovolné dávkové příkazy a také řešení proměnných MSBuild. Další informace najdete v tématu [postupy: nastavení příkazů nasazení služby SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Příkazový řádek před nasazením|Určuje, které příkazy se spustí před nasazením řešení SharePoint. Tento řádek podporuje libovolné dávkové příkazy a také řešení proměnných MSBuild. Další informace najdete v tématu [postupy: nastavení příkazů nasazení služby SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Soubor projektu|Název souboru obsahujícího sestavení, konfiguraci a další informace o projektu.|  
|Složka projektu|Umístění souboru projektu v systému. (Jen pro čtení.)|  
|Řešení v izolovaném prostoru|Určuje, zda by měl být projekt nasazen jako *řešení v izolovaném prostoru*, označované také jako *uživatel vytvořil řešení*. Řešení v izolovaném prostoru nejsou nutně důvěryhodná. Hodnota **true** znamená, že projekt je nasazen jako řešení v izolovaném prostoru, hodnota **false** znamená, že projekt je nasazen jako řešení farmy. Další informace najdete v tématu [v izolovaném prostoru aspekty řešení](../sharepoint/sandboxed-solution-considerations.md) a [rozdíly mezi řešeními v izolovaném prostoru a řešení ve farmách](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|Adresa URL webu|Určuje, [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] cílového webu pro tento projekt.|  
|Spouštěcí položka|Určuje první položku v projektu pro spuštění.|  
  
 Pokud zvolíte soubor položky služby SharePoint (například pracovní postup nebo funkce v uzlu funkce), se zobrazí v okně Vlastnosti následující vlastnosti:  
  
### <a name="project-item-properties"></a>Vlastnosti položky projektu
  
|Název vlastnosti|Popis|  
|-------------------|-----------------|  
|Řešení konfliktů při nasazení|Určuje akci, která má provést při nasazování položky projektu, jejích vlastnosti jsou stejné jako ty položky již na serveru. Další informace najdete v tématu [řešení potíží s balení a nasazení SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Vlastnosti funkce|Určuje sadu hodnot (uložených jako páry klíč hodnota), která je součástí funkce při nasazování do služby SharePoint. Po nasazení funkce můžete přistupovat hodnoty vlastností v kódu. Další informace najdete v tématu [poskytuje balení a informace o nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Příjemce funkce|Poskytuje kód, který se spustí při výskytu určitých událostí položky projektu obsahující funkci. Další informace najdete v tématu [poskytuje balení a informace o nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Název složky|Název složky položky Sharepointového projektu.|  
|Odkazy na výstup projektu|Určuje závislost, jako je například sestavení, které položky projektu je potřeba spustit. Další informace najdete v tématu [poskytuje balení a informace o nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Položky bezpečného řízení|Určuje ovládací prvky, které lze bezpečně upravovat nedůvěryhodnými uživateli. Další informace najdete v tématu [poskytuje balení a informace o nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Položka projektu vlastnosti souboru
  
|Název vlastnosti|Popis|  
|-------------------|-----------------|  
|Akce sestavení|Určuje, jak soubor souvisí s procesy sestavení a nasazení. Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Kopírovat do výstupního adresáře|Určuje, zda zdrojové soubory budou zkopírovány do výstupního adresáře. Může být jedna z následujících hodnot:<br /><br /> -   *Nekopírovat*<br />-   *Vždy kopírovat*<br />-   *Kopírovat, pokud je novější*<br /><br /> Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Vlastní nástroj|Určuje název nástroje, pokud existuje, který transformuje soubor v době návrhu a umístí výstup transformace do jiného souboru. Například datovou sadu (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) soubor má vlastní výchozí nástroj. Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Custom Tool Namespace|Obor názvů, do kterého je zkopírován výstup vlastního nástroje. Další informace najdete v tématu [vlastnosti souboru](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Umístění nasazení|Plně kvalifikovanou cestu souboru na Sharepointovém serveru. Tato cesta se skládá z kořene nasazení a cesty nasazení podvlastností.|  
|Cesta nasazení|Relativní cesta souboru v souboru SharePoint Server, jako je například Workflow1\\. Plně kvalifikovanou cestu k souboru se vytváří zřetězením *cesty nasazení* hodnotu na konec objektu *kořen nasazení* hodnotu.<br /><br /> Výběrem hodnoty z *RootFile* pro *typ nasazení* změny vlastností *kořen nasazení* vlastnost \<SharePointRoot >\\výsledkem plně kvalifikovanou cestu z \<SharePointRoot > \Workflow1\\. Další informace najdete v tématu [balení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Kořen nasazení|řetězec. Kořenové složky, kde je soubor nasazen na serveru SharePoint. Například \<SharePointRoot > \Template\Features\\\<FeatureName >\\.<br /><br /> Hodnota *kořen nasazení* vlastnost je určena *typ nasazení* nastavení.|  
|Typ nasazení|Typ nasazení souboru, který určuje jeho *kořen nasazení* hodnotu. Může být jedna z následujících hodnot:<br /><br /> NoDeployment:  *\<žádná hodnota >*<br /><br /> ElementManifest:  *\<SharePointRoot > \Template\Features\\\<FeatureName >*\\<br /><br /> ElementFile:  *\<SharePointRoot > \Template\Features\\\<FeatureName >\\*<br /><br /> TemplateFile:  *\<SharePointRoot > \Template\\*<br /><br /> RootFile:  *\<SharePointRoot >\\*<br /><br /> GlobalResource:  *\<SharePointRoot > \Resources\\*<br /><br /> ClassResource:  *\<ClassResourcePath >\\*<br /><br /> Další informace naleznete v tématu <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Název souboru|Název souboru nebo složky pro soubor položky.|  
|Úplná cesta|Umístění souboru pro položku. (Jen pro čtení.)|  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Šablony projektů a položek projektů služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)|Popisuje projekt služby SharePoint a šablony položek projektu, které [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Postupy: Přidání položek do projektu služby SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Popisuje, jak přidat nové nebo existující položky do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.|  
|[Návod: Vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Vás krok za krokem při vytváření zákazník pole, typ obsahu, definici seznamu a instanci seznamu.|  
|[Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)|Popisuje, jak přidat přijímače událostí pro projekt vytvořený v [návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Popisuje, jak vytvořit projekty pracovního postupu, který obsahuje formuláře přidružení pracovního postupu a formuláře zahájení pracovního postupu.|  
|[Vytváření stránek pro službu SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Popisuje, jak můžete vytvořit stránky jako je například stránky aplikace, weby, stránky předlohy a rozložení stránek pro službu SharePoint.|  
|[Vytvoření webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Popisuje, jak přidat ovládací prvky, které umožňují uživatelům přímo upravit obsah, vzhled a chování stránky webu služby SharePoint pomocí prohlížeče.|  
|[Vytvoření opakovaně použitelné ovládací prvky webové části nebo stránky aplikace](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Popisuje, jak vytvořit uživatelské ovládací prvky, které mohou být spotřebovány stránkami aplikace a webové části, která spustí v Sharepointu.|  
|[Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Popisuje, jak integrovat data z webové služby a back endové serverové aplikace do aplikace služby SharePoint.|  
|[Vytváření definic webu pro službu SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Popisuje, jak vytvořit definice webu: šablony, které se používají k vytváření webů služby SharePoint.|  
|[Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Popisuje, jak importovat položky, jako jsou moduly a typy obsahu z existujícího webu SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu služby SharePoint.|  
|[Vložení souborů do řešení pomocí modulů](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Popisuje způsob použití modulů k nasazení souborů z vašeho [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu web služby SharePoint.|  
|[Procházet připojení služby SharePoint pomocí Průzkumníka serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Popisuje, jak procházet místní weby služby SharePoint pomocí Průzkumníka serveru.|  
|[Zadání informací o balení a nasazení v položkách projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Popisuje způsob použití vlastností položek projektu k poskytnutí informací o balení a nasazení pro projekty, jako jsou položky bezpečného řízení, odkazy na výstup projektu a vlastnosti funkcí.|  
|[Postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Popisuje, jak mapované složky mohou být přidány do projektu a zajistit tak snadnější přístup k prostředkům služby SharePoint.|  
|[Aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md)|Popisuje problémy spojené s řešeními v izolovaném prostoru.|  
|[Zabezpečení pro řešení služby SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Popisuje aspekty zabezpečení pro vývoj řešení služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Dialogové okno pro výběr adresy URL &#40;vývoj pro SharePoint v sadě Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Popisuje dialogové okno, které můžete použít k přidání cest odkazů na prostředky ve vašem projektu nebo na místním serveru SharePoint.|  
  
## <a name="see-also"></a>Viz také:
 [Začínáme &#40;vývoj pro SharePoint v sadě Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Procházet připojení služby SharePoint pomocí Průzkumníka serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
