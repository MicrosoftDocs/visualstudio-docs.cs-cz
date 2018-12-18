---
title: Řešení potíží s řešeními služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f68f6e50be569df6130f7e6c6f3aa4bc7c107214
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296044"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Řešení potíží s řešeními služby SharePoint
  S těmito problémy nebo výstrah může dojít při ladění řešení služby SharePoint pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladicího programu. Další informace najdete v tématu [ladění řešení pracovního postupu služby SharePoint 2007](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Omezení tokenu v izolovaném prostoru vizuální webové části
 Vizuální webové části v řešení v izolovaném prostoru nemůže zpracovat standardní tokeny, například $SPUrl, který podporuje modul runtime služby SharePoint. V důsledku toho adresa URL není vyřešený a pokud se na ni můžete odkazovat přímo v prvku skriptu, jako v následujícím příkladu není možné zobrazit náhled obsahu v návrhovém zobrazení v Návrháři vizuální webové části:  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Chcete-li toto omezení obejít a analyzovat token, na něj odkazovat pomocí literálů:  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Omezení pro znaky v názvech projektů a položek projektu
 Názvy projektů a položek projektu může obsahovat pouze znaky, které jsou platné v cestě nasazení v SharePoint 2010. Žádná ostatní znaky jsou povoleny.  
  
### <a name="error-message"></a>Chybová zpráva
 Chybová zpráva "Neplatné znaky".  
  
### <a name="resolution"></a>Rozlišení  
 Názvy projektů služby SharePoint a položky projektu používejte pouze následující znaky:  
  
- Alfanumerické znaky ASCII  
  
- Místo  
  
- Tečka (.)  
  
- Čárka (,)  
  
- Podtržítko (_)  
  
- Pomlčky (-)  
  
- Zpětné lomítko (\\)  
  
  Když je zabalená do projektu, ověřovací pravidlo ověří, že vlastnost cesty nasazení pro každý soubor, který nasazujete obsahuje pouze tyto platné znaky.  
  
## <a name="errors-when-creating-custom-fields"></a>Chyby při vytváření vlastního pole
 V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vlastní pole jsou definována ve formátu XML. Pokud pole nejsou definována nebo odkazována pomocí konkrétní formátu, může dojít k chybám.  
  
### <a name="error-message"></a>Chybová zpráva
 Chybová zpráva "Neplatné znaky" v době vytváření balíčků.  
  
### <a name="resolution"></a>Rozlišení  
 ID pro definici pole musí být identifikátor GUID uzavřeny ve složených závorkách, jako v následujícím příkladu:  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Jak ukazuje následující příklad, odkazy na pole v typu obsahu musí být definován pomocí formátu prázdného elementu (\<FieldRef / >), nikoli pomocí elementů (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Chyba "nelze analyzovat soubor" nastane, pokud zdrojového kódu XML pro pole je poškozený, není platný soubor XML nebo nějaký jiný problém projevuje.  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nové definice lokality jiné než anglické jazykové nezobrazí na stránce vytváření webu po nasazení
 Po vytvoření a nasazení definice webu pomocí jiné než anglické jazykové verzi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (to znamená, že verzi s národním prostředím [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] než 1033), **přizpůsobení Sharepointu** nezobrazujekarta**Výběr šablony** pole a nové šablony webu se nezobrazí v **novému Sharepointovému webu** stránky.  
  
### <a name="error-message"></a>Chybová zpráva
 Žádné  
  
### <a name="resolution"></a>Rozlišení  
 K tomuto problému dochází kvůli nesprávné hodnotě v **cesta** vlastnost pro nastavení definice lokality webtemp soubor, třeba *webtemp_SiteDefinitionProject1.xml*. V **cesta** vlastnost souboru webtemp umístěna ve složce **umístění nasazení**, změňte 1033 na odpovídající národní prostředí [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Například použití japonské národní prostředí změňte hodnotu na 1041. Další informace najdete v tématu [ID národního prostředí přiřazené společností Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561).  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Zobrazí se chyba při nasazení projektu pracovního postupu na vyčištění systému
 K tomuto problému dochází, pokud provádíte nasazení projektu pracovního postupu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] čisté systému. Vyčistit systém je počítač, který obsahuje novou instalaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a SharePoint, ale žádné projekty nasazené pracovního postupu.  
  
### <a name="error-message"></a>Chybová zpráva
 Nejde najít seznamu služby SharePoint: historie pracovního postupu.  
  
### <a name="resolution"></a>Rozlišení  
 K této chybě dochází z důvodu chybějící seznamu historie pracovního postupu. Vzhledem k tomu, že vývojové prostředí je vyčistit systém, jsou nasazené žádné pracovní postupy a seznamu historie pracovního postupu dosud neexistuje. Pokud chcete tento problém vyřešit, otevřete pracovní postup průvodce, který způsobí, že se seznamu historie pracovního postupu chcete vytvořit.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>Chcete znovu zadat pracovní postup Průvodce  
  
1.  V **Průzkumníka řešení**, zvolte uzel pracovní postup.  
  
2.  V **vlastnosti** okna, klikněte na tlačítko tří teček (...) na jakákoli vlastnost, která obsahuje tlačítko se třemi tečkami.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Uživatel musí aktualizovat stránku aplikace v prohlížeči při ladění, chcete-li zobrazit aktualizovanou bitovou kopii
 Pokud ladíte řešení služby SharePoint, která obsahuje stránku aplikace s ovládacím prvkem, který zobrazuje obrázek, například [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] ovládací prvek obrázku, je nutné aktualizovat stránku v prohlížeči zobrazit všechny změny, které byly provedeny do bitové kopie.  
  
## <a name="error-the-site-location-is-not-valid"></a>Chyba: Umístění webu je neplatný
 Tento problém může nastat, pokud [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] není nainstalována. Může také dojít, pokud nemáte přístup správce k webu SharePoint, který je zadán v **Průvodce přizpůsobením SharePoint**.  
  
### <a name="error-message"></a>Chybová zpráva
  
-   Umístění webu služby SharePoint není platný.  
  
### <a name="resolution"></a>Rozlišení  
  
-   Nainstalujte [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Ujistěte se, že máte přístup správce k webu SharePoint. Další informace najdete v tématu [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] Online článku [přiřadit nebo odebrat správce aplikací služeb v produktu SharePoint Server](https://docs.microsoft.com/sharepoint/administration/assign-or-remove-administrators-of-service-applications).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Lokality odstranění webové události nedochází v projektu příjemce událostí
 Když vytvoříte projekt příjemce událostí a výběru určitých webových událostí jako "Web se odstraňuje", události se nikdy neprovádí.  
  
### <a name="error-message"></a>Chybová zpráva
 Žádné  
  
### <a name="resolution"></a>Rozlišení  
 K tomuto problému dochází, protože obor funkcí musí být "Web" pro zpracování událostí na úrovni webu, ale výchozí obor funkce pro projekty přijímač událostí je "Web". Vliv na webové události jsou:  
  
- Web se odstraní (WebDeleting)  
  
- Byl odstraněn web (WebDeleted)  
  
- Web se přesunout (WebMoving)  
  
- Byl přesunut web (WebMoved)  
  
  Chcete-li vyřešit tento problém, Změna oboru funkce příjemce událostí následujícím způsobem.  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Chcete-li změnit obor funkcí příjemce událostí  
  
1.  V **Průzkumníku řešení**, otevřete příjemce událostí *.feature* soubor **návrháře funkcí** dvojitým kliknutím na soubor nebo otevřením jeho místní nabídky a pak Výběr **otevřít**.  
  
2.  Klikněte na šipku vedle položky **oboru**a klikněte na tlačítko **lokality** v seznamu, který se zobrazí.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Po změně názvu identifikátoru v projektu model připojení obchodních dat se zobrazí chyba nasazení
 K tomuto problému dochází, pokud změníte název identifikátoru entity v modelu služby Připojení obchodních dat (BDC) a potom se pokuste nasazení řešení.  
  
### <a name="error-messages"></a>Chybové zprávy
  
-   \<*Název modelu*> má následující aktivační chyby externího typu obsahu...  
  
-   Rozhraní IMetadataObject s názvem "\<*název modelu*>" má hodnotu v poli "name", který je duplicitní...  
  
### <a name="resolution"></a>Rozlišení  
 Chcete-li tento problém vyřešit, odstraňte ručně modelu a pak nasazení řešení.  Model můžete odstranit pomocí některé z následujících nástrojů:  
  
-   Centrální správy služby SharePoint 2010. Další informace najdete v tématu [správy modelu služby BDC](http://go.microsoft.com/fwlink/?LinkID=181472) na webové stránce Microsoft TechNet.  
  
-   Prostředí Windows PowerShell. Můžete odstranit model zadáním následujícího příkazu na příkazovém řádku: **odebrat SPBusinessDataCatalogModel**. Další informace najdete v tématu [obecné rutiny (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) na webové stránce Microsoft TechNet.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Objeví se chyba při pokusu o zobrazení vizuální webové části služby SharePoint
 K tomuto problému dochází při **cesta** vlastnosti uživatelského ovládacího prvku nezačíná řetězcem "CONTROLTEMPLATES\\".  
  
### <a name="error-messages"></a>Chybové zprávy
  
-   Soubor "/_CONTROLTEMPLATES/*\<název projektu >*/*\<název webové části >*/*\<uživatelského ovládacího prvku název >*.ascx "neexistuje.  
  
-   Chyba serveru v aplikaci '/'.  
  
### <a name="resolution"></a>Rozlišení  
  
##### <a name="to-resolve-this-issue"></a>Chcete-li vyřešit tento problém  
  
1.  V **Průzkumníka řešení**, zvolte souboru uživatelského ovládacího prvku, jejichž přípona názvu souboru je *.ascx*.  
  
2.  V panelu nabídky zvolte **zobrazení** > **okno vlastností**.  
  
3.  V **vlastnosti** okna, rozbalte **umístění nasazení** uzlu.  
  
4.  Ujistěte se, že hodnota **cesta** vlastnost začíná řetězcem "CONTROLTEMPLATES\\".  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Chyba se zobrazí při spuštění importované opakovaně použitelného pracovního postupu, obsahující pole formuláře úkolu.
 K tomuto problému dochází, pokud provedete import pracovní postup, který obsahuje formulář úkol, který obsahuje pole a pak spusťte nový pracovní postup ve stejném systému, ze kterého jste ho naimportovali.  
  
### <a name="error-message"></a>Chybová zpráva
 V kroku nasazení 'Aktivace funkce' došlo k chybě: pole s Id [*Guid*] definované ve funkci [*Guid*] nebyla nalezena v aktuální kolekci webů nebo v lokalitě.  
  
### <a name="resolution"></a>Rozlišení  
 Tato chyba je výsledek kolizí pole ID, které způsobeny tím, že Import opakovaně použitelných pracovních postupů projekt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nedojde ke změně pole formuláře úkolu ID. Pokud provádíte nasazení importovaných pracovních postupů na stejném serveru, který obsahuje původní pracovního postupu, dojde k kolize ID pole.  
  
 Chcete-li vyřešit tento problém, použijte funkci Najít a nahradit Chcete-li změnit hodnotu atributu ID pole ve všech souborech importovaných pracovních postupů.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Zobrazí se chyba při importu byl přejmenován, že je spuštěna instance seznamu
 K tomuto problému dochází, je-li přejmenovat instance importované seznamu a pak ho spusťte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### <a name="error-message"></a>Chybová zpráva
 Chyba sestavení: v kroku nasazení 'Aktivace funkce' došlo k chybě: soubor Template\Features\\[*Importovat projekt*<em>funkce</em>*název*] \Files\Lists \\[*staré*<em>název seznamu</em>] \Schema.xml neexistuje.  
  
### <a name="resolution"></a>Rozlišení  
 Při importu instance seznamu se atribut s názvem CustomSchema se přidá do souboru Elements.xml instanci seznamu. Elements.XML obsahuje cestu k vlastní schema.xml pro instanci seznamu. Pokud přejmenujete instance seznamu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], se změní cesta pro vlastní schema.xml nasazení, ale cesta hodnota atributu CustomSchema je aktualizována. V důsledku toho nelze najít instanci seznamu *schema.xml* souboru v původní cestě, která je zadaná atributem CustomSchema, když je funkce aktivovaná.  
  
 Pokud chcete tento problém vyřešit, aktualizujte cestu umístění nasazení *schema.xml* souboru v atributu CustomSchema.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint ladicí relace ukončen službou IIS.
 K tomuto problému dochází, pokud nastavíte zarážku [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení služby SharePoint, zvolte **F5** klávesy spusťte ji a potom zůstat na zarážce delší než 90 sekund.  
  
### <a name="error-message"></a>Chybová zpráva
 Byl ukončen proces webového serveru, který byl laděn Internetové informační služby (IIS). Je-li předejít tomuto problému, konfigurace nastavení příkazu ping fondu aplikací ve službě IIS. Najdete v nápovědě.  
  
### <a name="resolution"></a>Rozlišení  
 Ve výchozím nastavení fond aplikací IIS čeká 90 sekund pro aplikaci reagovat dříve, než ho ukončí aplikaci. Tento proces se označuje jako "příkazy ping" aplikace. Pokud chcete tento problém vyřešit, můžete zvýšit dobu čekání nebo zakázat aplikaci zcela příkazu ping.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>Pro přístup k nastavení fondu aplikací služby IIS  
  
1.  Otevřete Správce služby IIS.  
  
2.  V **připojení** podokně rozbalte uzel serveru SharePoint a klikněte na tlačítko **fondy aplikací** uzlu.  
  
3.  Na **fondy aplikací** zvolte fond aplikací služby SharePoint (obvykle "SharePoint - 80") a pak na **akce** podokně, vyberte **Upřesnit nastavení** odkaz.  
  
4.  Pokud chcete zvýšit dobu čekání před vypršením časového limitu služby IIS, změňte hodnotu vlastnosti **maximální prodleva příkazu Ping (v sekundách)** na hodnotu, která je větší než 90 sekund.  
  
5.  Chcete-li zakázat příkazy ping služby IIS, nastavte **povolený příkaz Ping** k **False**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Automatické odvolání opustí instance odděleného seznamu ve službě SharePoint
 K tomuto problému dochází, pokud je provést následující kroky.  
  
1.  Vytvoření definice seznamu, který má instance seznamu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zvolte **F5** spusťte řešení.  
  
3.  Zastavit ladění, nebo zavřete webu služby SharePoint.  
  
4.  Otevřete web služby SharePoint a otevřete instanci seznamu.  
  
### <a name="error-message"></a>Chybová zpráva
 Chyba serveru v aplikaci '/'.  
  
### <a name="resolution"></a>Rozlišení  
 Proto po ukončení relace ladění řešení služby SharePoint, která automatické odvolání funkce odvolá řešení. Při odvolání odstraní definici seznamu SharePoint, ale nedojde k odstranění instance seznamu. Základní definici seznamu vyžaduje instanci seznamu.  
  
 Chcete-li vyřešit tento problém, nasaďte řešení, na panelu nabídek, výběrem **sestavení** > **nasadit**. (Neladit řešení kliknutím **F5** klíč.) Odstraňte instanci seznamu v Sharepointu.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Exportované verze nahrazuje původní řešení služby SharePoint
 Pokud exportujete řešení služby SharePoint, řešení do importovat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]a pak nasadíte řešení zpět do stejné lokality, ze kterého byl exportován, se nahradí původní řešení služby SharePoint. Tomuto problému nedojde-li nasadit řešení na serveru, který nemá v původním řešení aktivovat na něj.  
  
### <a name="error-message"></a>Chybová zpráva
 Žádné  
  
### <a name="resolution"></a>Rozlišení  
 Aby nedošlo k přepsání řešení na webu, ze kterého byl exportován, změňte identifikátory GUID SolutionID a ID funkce všechny importované funkce [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu.  
  
## <a name="error-appears-when-debugging-starts"></a>Chyba se zobrazí při spuštění ladění
 Při spuštění ladění řešení služby SharePoint v sadě Visual Studio, chyba naznačuje, že Visual Studio nelze načíst soubor Web.config, protože nebyl zadaný klíč ve slovníku.  
  
### <a name="error-message"></a>Chybová zpráva
 Nepovedlo se načíst konfigurační soubor Web.config. Nějaké nesprávné elementy XML v souboru a zkuste to znovu. Došlo k následující chybě: daný klíč není k dispozici ve slovníku.  
  
### <a name="resolution"></a>Rozlišení  
 Chcete-li vyřešit tento problém, ujistěte se, že hodnotu vlastnosti Adresa URL webu projektu služby SharePoint v sadě Visual Studio odpovídá adresu URL, která je přiřazena k výchozí zóna pro mapování alternativních adres URL webové aplikace. Chyba nelze vyřešit pomocí jiné zóny, jako je například Intranet, adresy URL. Web adresu URL pro projekt a adresu URL ve výchozí zóně se musí shodovat. Pro přístup k mapování alternativních adres URL, spusťte nástroj pro centrální správy služby SharePoint 2010, zvolte **správy aplikací** odkaz a pak v části **webových aplikací**, zvolte  **Konfigurace alternativních mapování přístupu** odkaz. Další informace najdete v tématu [vytváření zón pro webové aplikace](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Viz také:
 [Řešení potíží s balení a nasazení SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
