---
title: Import položek z existující stránky SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7435d6c7ad210554031994f4a366812f9799ffb2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832101"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Import položek z existující stránky SharePoint
  Šablona projektu importovat balíček řešení služby SharePoint, můžete znovu použít prvky, jako jsou typy obsahu a pole z existujících webů služby SharePoint v novém [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení služby SharePoint. Ačkoli můžete spustit nejvíce importované řešení bez jakýchkoli úprav, existují určitá omezení a problémy, které byste měli zvážit, zejména v případě, že upravíte všechny položky po importu.  
  
> [!NOTE]  
>  Pro import opakovaně použitelných pracovních postupů, použijte šablonu projektu Import opakovaně použitelného pracovního postupu. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Pokyny pro import opakovaně použitelných pracovních postupů](../sharepoint/guidelines-for-importing-reusable-workflows.md).  
  
## <a name="supported-sharepoint-solutions"></a>Podporované řešení služby SharePoint
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] plně podporuje import řešení vytvořená v [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] a [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] nepodporuje import řešení vytvořená v následujících aplikacích:  
  
- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
- Microsoft SharePoint Designer 2007  
  
- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
  I když můžete často úspěšně importovat řešení vytvořené pomocí těchto aplikací, je, které tuto funkci nelze testovat a nepodporuje.  
  
## <a name="item-import-restrictions"></a>Omezení pro import položek
 I když většina položek služby SharePoint lze importovat z existující *.wsp* souboru následující položky nejsou podporovány a mohou vyžadovat změny fungovala správně:  
  
- Entity služby BDC  
  
- Kód prvky přidružení pracovního postupu.  
  
- Pracovní postupy kódu  
  
- Vizuální webové části (.ascx)  
  
- Webové služby (*.asmx*)  
  
- Typ obsahu vazby  
  
- Přijímače událostí  
  
- Seznam definic (šablony)  
  
- Definice webu  
  
  Při exportu řešení z [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], tyto položky jsou automaticky vyloučeny z *.wsp* souboru. Ale ostatní *.wsp* soubory vygenerované z nepodporované nástrojů mohou obsahovat tyto položky. (Viz "Řešení služby SharePoint nepodporuje" výše v tomto tématu.)  
  
## <a name="what-happens-when-you-import-a-solution"></a>Co se stane při importu řešení
 Když importujete šablonu importovat balíček řešení služby SharePoint, řešení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zkopíruje všechny obsah *.wsp* importovat soubor a pokusí sjednotit a uchovat libovolný počet přidružení a odkazů mezi prvky a jejich nejvíce souborů.  
  
 Zkopírujte všechny importované položky do odpovídající složky v **Průzkumníka řešení**. Například typy obsahu se zobrazí ve složce **typů obsahu** a instance seznamu se zobrazí v rámci **seznam instancí**. Soubory přidružené k importované položky jsou také zkopírovány do složky položky. Například instance importované seznam obsahuje její moduly, formuláře a stránky ASPX.  
  
### <a name="dependent-items"></a>Závislé položky
 Pokud vyberete položku v Průvodci importovat balíček řešení služby SharePoint, ale nikoli jeho závislé položky, okno se zprávou vás informuje, že závislé položky musí také vybrat před importem.  
  
### <a name="what-are-features"></a>Jaké jsou funkce?
 SharePoint Designer uživatelé mohou vidět neočekávané souborech s názvem *funkce*, se zobrazí v rámci svých importované řešení v **Průzkumníku řešení.** I když funkce existoval v řešení pro SharePoint Designer, byly skryté zobrazení. Funkce jsou nyní viditelné v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Funkce jsou kontejnery pro položky služby SharePoint. Jednotlivé funkce uchovává odkaz na každé položky, jako jsou typy obsahu a seznam definic, které obsahuje. Při importu řešení, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nastaví funkce pro všechny importované prvky a pokusí se údržbu relací elementu funkce pro soubory. Všechny soubory, jejichž odkazy nebylo možné přeložit jsou umístěny v **ostatní soubory importovat** složky.  
  
 Další informace o funkcích najdete v tématu [řešení pro vývoj SharePoint](../sharepoint/developing-sharepoint-solutions.md) a [práce s funkcemi](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
### <a name="handle-special-cases"></a>Zpracovat speciální případy
 V některých případech nejdou sjednotit sady Visual Studio položku s jeho závislých souborů. Všechny soubory, které [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nerozpoznala se zobrazí ve složce **ostatní soubory importovat**. Kromě toho jejich **DeploymentType** vlastnosti jsou nastaveny na **NoDeployment** tak, aby nejsou nasazené pomocí řešení.  
  
 Například pokud importujete definici seznamu ExpenseForms, definici seznamu s tímto názvem se zobrazí v části **seznam definic** složky **Průzkumníku řešení** spolu s jeho  *Elements.xml* a *Schema.xml* soubory. Ale přidruženy formuláře ASPX a HTML můžete umístit do složky s názvem **ExpenseForms** pod **ostatní soubory importovat** složky. K dokončení importu se přesunutí těchto souborů v rámci definice seznamu ExpenseForms v **Průzkumníka řešení** a změnit **DeploymentType** vlastnost pro každý soubor z **NoDeployment** k **ElementFile**.  
  
 Při importu přijímače událostí *Elements.xml* soubor je zkopírován do správného umístění, ale musíte ručně zahrnout do sestavení v balíčku řešení tak, aby ho nasadí s řešením. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] jak to udělat, najdete v článku [postupy: Přidání a odebrání dalších sestavení](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Při importu pracovních postupů, formuláře InfoPath se zkopírují do **ostatní soubory importovat** složky. Pokud *.wsp* soubor obsahuje šablonu, že je nastavena jako úvodní stránku v **Průzkumníka řešení**.  
  
## <a name="import-fields-and-property-bags"></a>Pole pro import a kontejnery objektů a dat
 Při importu řešení, které má více polí, všechny definice samostatné pole jsou sloučeny do jednoho *Elements.xml* souboru pod uzlem v **Průzkumníka řešení** volá **pole** . Podobně, sloučí všechny položky vlastnosti kontejneru objektů a dat *Elements.xml* souboru pod uzel nazvaný **PropertyBags**.  
  
 Pole v Sharepointu se sloupci zadaného datového typu, například text, logickou hodnotu nebo vyhledávání. Další informace najdete v tématu [stavebním blokem: sloupce a typy polí](http://go.microsoft.com/fwlink/?LinkId=182304). Kontejnery objektů a umožňují přidání vlastností do objektů v Sharepointu, všechno z farmy na seznam na Sharepointovém webu. Kontejnery objektů a jsou implementované jako zatřiďovací tabulku názvů a hodnot vlastností. Další informace najdete v tématu [Správa konfigurace služby SharePoint](http://go.microsoft.com/fwlink/?LinkId=182296) nebo [nastavení vlastnosti kontejneru objektů a dat služby SharePoint](http://go.microsoft.com/fwlink/?LinkId=182297).  
  
## <a name="delete-items-in-the-project"></a>Odstranit položky v projektu
 Většina položek v řešení služby SharePoint mít jednu nebo více závislých položek. Například instance seznamu závisí na typy obsahu a typy obsahu jsou závislé na pole. Po importu řešení služby SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] neupozorní jste žádné problémy s odkazem při odstranění položky v řešení, ale nikoli jeho závislé položky, dokud se při pokusu o nasazení řešení. Například pokud importované řešení má instanci seznamu, který závisí na typu obsahu a odstranit tento typ obsahu, může dojít k chybě při nasazení. Pokud není k dispozici na serveru SharePoint závislé položky dojde k chybě. Podobně pokud odstraněné položky má také kontejner souvisejících objektů, odstraňte tyto položky vlastnosti kontejneru objektů a dat z **PropertyBags** *Elements.xml* souboru. Proto pokud odstraníte všechny položky z importované řešení a dojde k chybám nasazení, zkontrolujte Pokud muset také odstraní všechny závislé položky.  
  
## <a name="restore-missing-feature-attributes"></a>Obnovit chybějící atributy funkce
 Při importu řešení, jsou vynechány některé atributy volitelná funkce z manifestu importované funkce. Pokud chcete obnovit tyto atributy v novém souboru funkce, identifikovat chybějící atributy porovnáním původní soubor funkce k manifestu nové funkce a postupujte podle pokynů v tématu [postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Neprovádí se u instance integrovaného seznamu zjišťování konfliktů nasazení
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] neprovádí zjišťování konfliktů nasazení na instance integrovaného seznamu (to znamená, výchozí seznam instancí, které jsou součástí Sharepointu). Aby nedošlo k přepsání instance integrovaného seznamu na Sharepointu se provádí není provádění zjišťování konfliktů. Předdefinovaného seznamu, které instance jsou stále nasazení nebo aktualizovat, ale jsou nikdy odstraněn nebo přepsat. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Řešení potíží s balení a nasazení SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="import-sharepoint-server-2010-workflows"></a>Importovat pracovní postupy služby SharePoint Server 2010
 Pokud importujete pracovní postup vytvořený v [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], nebude po nasazení správně fungovat. Pracovního postupu se nespustí správně, protože chybí některé sestavení a [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] pracovní postupy obsahují formuláře aplikace InfoPath, který aktuálně není podporován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení pracovního postupu. Však importovat [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] pracovních postupů můžete provést po opravě některé položky, jako je například přidávání odkazů na fungovala správně [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] sestavení a opětovné připojení formuláře InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Import pracovních postupech služby SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=182226).  
  
## <a name="item-name-character-limit"></a>Limit počtu znaků názvu položky
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] má limit 260 celkový počet znaků pro projekt a názvy položek projektu, včetně cesty. Při importu řešení, pokud název položky překročí tento limit, zobrazí chybová zpráva:  
  
 **Zadaná cesta, název souboru nebo obojí jsou příliš dlouhé. Plně kvalifikovaný název musí být kratší než 260 znaků a název adresáře musí být kratší než 248 znaků.**  
  
 Když se zobrazí tato chyba, není tato položka vytvořena. K tomuto problému dochází nejčastěji se importované moduly. K tomuto problému vyhnout, postupujte takto:  
  
-   Používejte krátké názvy pro váš projekt, zadejte je **přidat nový projekt** dialogové okno.  
  
-   Vytvoření projektu v umístění jako blízko kořenové složce co nejrychleji, aby zkrácení cesty.  
  
## <a name="the-sharepointproductversion-attribute"></a>Atribut SharePointProductVersion
 Při importu řešení vytvořené ve starší verzi služby SharePoint, jako [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] nebo [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], změňte hodnotu atributu SharePointProductVersion v manifestu balíčku 12.0 nebo vložit ovládací prvek správce skriptů do všech importovaných Web stránky a nechte SharePointProductVersion nastaven na 14.0. V opačném případě importované webových formulářů nezobrazí v Sharepointu.  
  
### <a name="background"></a>Pozadí  
 Řešení v [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] a [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] zahrnovat atribut s názvem SharePointProductVersion. SharePoint používá k určení verze služby SharePoint, řešení je navrženo pro tento atribut v manifestech jeho balíčku. Dvě platné hodnoty jsou 12.0 a 14.0. Hodnota 12.0 znamená, že položka je navržená pro [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] nebo [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]; hodnota 14.0 znamená, že položka je navržená pro [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Pro zvýšení zabezpečení při vykreslování stránky ASPX [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] a [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] vyžadovat, aby všechny ASPX nebo stránkách předlohy obsahovalo ovládací prvek správce skriptů. Další informace o správce skriptů, najdete v části [Přehled ovládacího prvku ScriptManager](http://go.microsoft.com/fwlink/?LinkID=169399). Proto není k dispozici v ovládacím prvku skript správce [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] a [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], jeden je nutné přidat do některé [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] nebo [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] stránka, která se upgraduje na [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Stránky ASPX, které používají standardní stránky předlohy nevyžadují ovládací prvek správce skriptů, protože jedna již byla přidána do standardní stránky předlohy. Ale stránky ASPX, která nepoužívají stránky předlohy nebo které využívají vlastní stránky předlohy musí přidat ovládací prvek skriptu fungování [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Neexistence ovládací prvek správce skriptů může být problém při importu [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] nebo [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] projektu do [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], protože atribut SharePointProductVersion všechny nové projekty je nastavena na 14.0. Pokud nasadíte upgradovaném projektu, který má webový formulář bez správce skriptů, formulář nezobrazí v Sharepointu.  
  
## <a name="see-also"></a>Viz také:
 [Návod: Import položek z existující stránky SharePoint](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [Pokyny pro import opakovaně použitelných pracovních postupů](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [Návod: Importujte opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  
