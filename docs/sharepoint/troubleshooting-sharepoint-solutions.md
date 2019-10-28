---
title: Řešení potíží s řešeními SharePoint | Microsoft Docs
ms.date: 02/22/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e8ccaaf877c04b3d58fc6d54bb658c2cef77b6f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985312"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Řešení potíží s řešeními služby SharePoint
  Při ladění řešení služby SharePoint pomocí ladicího programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mohou nastat následující problémy nebo výstrahy. Další informace najdete v tématu [ladění řešení pracovních postupů pro SharePoint 2007](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Omezení tokenů ve vizuálních webových částech v izolovaném prostoru
 Vizuální webové části v řešeních v izolovaném prostoru (sandbox) nemůžou zpracovávat standardní tokeny, jako je $SPUrl, které podporuje modul runtime služby SharePoint. V důsledku toho se adresa URL nevyřešila a nemůžete zobrazit náhled obsahu v zobrazení Návrh v Návrháři webové části, pokud se na něj odkazuje přímo v prvku skriptu, jako v následujícím příkladu:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Pokud chcete toto omezení obejít a vyřešit token, přečtěte si ho pomocí literálů:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Omezení znaků v názvech projektů a položek projektu
 Názvy projektů a položek projektu můžou obsahovat jenom znaky, které jsou platné v cestě nasazení v SharePointu 2010. Nejsou povoleny žádné jiné znaky.

### <a name="error-message"></a>Chybová zpráva
 Chybová zpráva "neplatné znaky".

### <a name="resolution"></a>Řešení
 Pro názvy projektů SharePoint a položek projektu použijte pouze následující znaky:

- Alfanumerické znaky ASCII

- Místo

- Tečka (.)

- Čárka (,)

- Podtržítko (_)

- Pomlčka (-)

- Zpětné lomítko (\\)

  Když je projekt zabalený, ověřovací pravidlo ověří, že vlastnost Deployment-Path pro každý soubor, který nasazujete, obsahuje jenom tyto platné znaky.

## <a name="errors-when-creating-custom-fields"></a>Chyby při vytváření vlastních polí
 V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]jsou vlastní pole definována v XML. Pokud pole není definováno nebo není odkazováno pomocí konkrétního formátu, může dojít k chybám.

### <a name="error-message"></a>Chybová zpráva
 Chybová zpráva "neplatné znaky" v době balení.

### <a name="resolution"></a>Řešení
 ID pro definici pole musí být identifikátor GUID uzavřený ve složených závorkách, jak ukazuje následující příklad:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Jak ukazuje následující příklad, odkaz na pole v typu obsahu musí být definován pomocí prázdného formátu elementu (\<FieldRef/>), nikoli pomocí elementů Start/end (\<FieldRef >\</FieldRef >):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Pokud je zdrojový kód XML pro pole poškozený, není platný soubor XML nebo se projeví nějaký jiný problém, dojde k chybě "nelze analyzovat soubor".

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nové definice v jiné než anglické lokalitě se po nasazení nezobrazí na stránce pro vytvoření webu.
 Když vytvoříte a nasadíte definici webu pomocí jiné než anglické verze [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (tj. verze s národním prostředím [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] jinou než 1033), karta **přizpůsobení SharePointu** se nezobrazí v poli pro **Výběr šablony** a na novém webu. Šablona se nezobrazí na **nové stránce webu služby SharePoint** .

### <a name="error-message"></a>Chybová zpráva
 Žádné

### <a name="resolution"></a>Řešení
 K tomuto problému dochází z důvodu nesprávné hodnoty ve vlastnosti **path** pro konfigurační soubor definice webu WebTemp, například *webtemp_SiteDefinitionProject1. XML*. Ve vlastnosti **cesta** k souboru WebTemp, který je umístěn v **umístění nasazení**, změňte 1033 na příslušné národní prostředí [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Například pro použití japonského národního prostředí změňte hodnotu na 1041. Další informace najdete v tématu [ID národního prostředí přiřazené společností Microsoft](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Při nasazení projektu pracovního postupu v čistém systému se zobrazí chyba
 K tomuto problému dochází, pokud nasadíte projekt pracovního postupu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] v čistém systému. Čistý systém je počítač, který má novou instalaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a SharePointu, ale nenasazené projekty pracovního postupu.

### <a name="error-message"></a>Chybová zpráva
 Nejde najít SharePointový seznam: historie pracovního postupu.

### <a name="resolution"></a>Řešení
 K této chybě dochází z důvodu chybějícího seznamu historie pracovního postupu. Vzhledem k tomu, že vývojové prostředí je čistým systémem, nejsou nasazené žádné pracovní postupy a seznam historie pracovního postupu ještě neexistuje. Chcete-li tento problém vyřešit, spusťte znovu Průvodce pracovním postupem, který způsobí vytvoření seznamu historie pracovního postupu.

##### <a name="to-reenter-the-workflow-wizard"></a>Postup pro znovu zadat průvodce pracovním postupem

1. V **Průzkumník řešení**vyberte uzel pracovního postupu.

2. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami (...) u libovolné vlastnosti, která má tlačítko se třemi tečkami.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Uživatel musí aktualizovat stránku aplikace v prohlížeči během ladění, aby zobrazil aktualizovaný obrázek.
 Pokud ladíte řešení služby SharePoint, které obsahuje stránku aplikace s ovládacím prvkem, který zobrazuje obrázek, například [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] ovládací prvek obrázek, je nutné aktualizovat stránku v prohlížeči, aby se zobrazily všechny změny provedené v obrázku.

## <a name="error-the-site-location-is-not-valid"></a>Chyba: umístění webu je neplatné.
 K tomuto problému může dojít, pokud není nainstalováno [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Tato situace může nastat také v případě, že nemáte přístup správce k webu služby SharePoint, který je uveden v **Průvodci vlastním nastavením služby SharePoint**.

### <a name="error-message"></a>Chybová zpráva

- Umístění webu služby SharePoint je neplatné.

### <a name="resolution"></a>Řešení

- Nainstalujte [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Ujistěte se, že máte přístup správce k webu služby SharePoint. Další informace najdete v článku [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] online v tématu [přiřazení nebo odebrání správců aplikací služby na serveru SharePoint](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Webová událost odstranění webu se nevyskytuje v projektu přijímače událostí.
 Když vytvoříte projekt příjemce událostí a vyberete určité webové události, jako je například "web se odstraňuje", událost se nikdy nestane.

### <a name="error-message"></a>Chybová zpráva
 Žádné

### <a name="resolution"></a>Řešení
 K tomuto problému dochází, protože obor funkce musí být "Web" pro zpracování událostí na úrovni webu, ale výchozí obor funkce pro projekty přijímače událostí je "Web". Ovlivněné webové události jsou:

- Probíhá odstraňování webu (webové odstranění).

- Lokalita se odstranila (webodstranila).

- Probíhá přesun webového serveru (webový přesun).

- Webový server byl přesunut (webový přesunutý).

  Chcete-li tento problém vyřešit, změňte rozsah funkcí přijímače událostí, a to následujícím způsobem.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Změna rozsahu funkcí přijímače událostí

1. V **Průzkumník řešení**otevřete soubor *. Feature* příjemce události v **Návrháři funkcí** Poklikáním na soubor nebo otevřením jeho místní nabídky a následným výběrem možnosti **otevřít**.

2. Vyberte šipku vedle možnosti **Rozsah**a potom v seznamu, který se zobrazí, vyberte možnost **lokalita** .

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Po změně názvu identifikátoru v projektu modelu připojení obchodních dat se zobrazí chyba nasazení.
 K tomuto problému dochází, pokud změníte název identifikátoru entity v modelu služby připojení obchodních dat (BDC) a pak se pokusíte nasazení řešení nasadit.

### <a name="error-messages"></a>Chybové zprávy

- *název \<modelu*> obsahuje následující chyby aktivace typu externího obsahu...

- IMetadataObject s názvem\<*název modelu*> obsahuje hodnotu v poli Name, která je duplikována...

### <a name="resolution"></a>Řešení
 Chcete-li tento problém vyřešit, odstraňte model ručně a pak znovu nasaďte řešení.  Model můžete odstranit pomocí některého z následujících nástrojů:

- Centrální správa SharePoint 2010 Další informace najdete v tématu [Správa modelů BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#deleteamodel) na webu Microsoft TechNet.

- Prostředí Windows PowerShell. Tento model můžete odstranit zadáním tohoto příkazu na příkazovém řádku: **Remove-SPBusinessDataCatalogModel**. Další informace najdete v tématu [Obecné rutiny (SharePoint Server 2010)](/powershell/module/sharepoint-server/&view=sharepoint-ps) na webu Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Při pokusu o zobrazení vizuální webové části na SharePointu se zobrazí chyba
 K tomuto problému dochází, pokud vlastnost **path** uživatelského ovládacího prvku nezačíná řetězcem "CONTROLTEMPLATES\\".

### <a name="error-messages"></a>Chybové zprávy

- Soubor '/_CONTROLTEMPLATES/ *\<projektu název >* / *\<název webové části >* /\<*název uživatelského ovládacího prvku >* . ascx neexistuje.

- Chyba serveru v aplikaci/

### <a name="resolution"></a>Řešení

##### <a name="to-resolve-this-issue"></a>Řešení tohoto problému

1. V **Průzkumník řešení**vyberte soubor uživatelského ovládacího prvku, jehož přípona názvu souboru je *. ascx*.

2. Na panelu nabídek vyberte možnost **zobrazit** > **okno Vlastnosti**.

3. V okně **vlastnosti** rozbalte uzel **umístění nasazení** .

4. Ujistěte se, že hodnota vlastnosti **path** začíná řetězcem "CONTROLTEMPLATES\\".

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Chyba se zobrazí při spuštění importovaného opakovaně použitelného pracovního postupu, který obsahuje pole formuláře úkolu.
 K tomuto problému dochází, když naimportujete pracovní postup, který obsahuje formulář úkolu s polem, a potom spustíte nový pracovní postup ve stejném systému, ze kterého jste ho naimportovali.

### <a name="error-message"></a>Chybová zpráva
 Došlo k chybě v kroku nasazení – aktivovat funkce: v aktuální kolekci webů nebo v podřízeném webu bylo nalezeno pole s ID [*GUID*] definované v součásti [*GUID*].

### <a name="resolution"></a>Řešení
 Tato chyba je výsledkem kolizí ID polí, ke kterým dochází, protože projekt import opakovaně použitelného pracovního postupu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nemění ID polí formuláře úlohy. Pokud nasadíte importovaný pracovní postup na stejný server, který obsahuje původní pracovní postup, dojde k kolizím ID polí.

 Chcete-li tento problém vyřešit, změňte hodnotu atributu ID pole ve všech importovaných souborech pracovního postupu pomocí funkce Find a Replace.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Při spuštění přejmenované instance importovaného seznamu se zobrazí chyba
 K tomuto problému dochází, Pokud přejmenujete importovanou instanci seznamu a potom ji spustíte v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

### <a name="error-message"></a>Chybová zpráva
 Chyba sestavení: došlo k chybě v kroku nasazení ' aktivovat funkce ': soubor Template\Features\\[*Import* *názvu*funkce projektu] \Files\Lists\\[<em>název seznamu</em>Old] \Schema.xml neexistuje.

### <a name="resolution"></a>Řešení
 Při importu instance seznamu se do souboru Elements. XML instance seznamu přidá atribut s názvem CustomSchema. Elements. XML obsahuje cestu k vlastnímu schématu. XML pro instanci seznamu. Při přejmenování instance seznamu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]se změní cesta nasazení pro vlastní schéma. XML, ale hodnota cesty atributu CustomSchema není aktualizována. V důsledku toho instance seznamu nemůže najít soubor *Schema. XML* ve staré cestě, která je určena atributem CustomSchema při aktivaci funkce.

 Chcete-li tento problém vyřešit, aktualizujte cestu k umístění nasazení souboru *Schema. XML* v atributu CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Služba IIS ukončila relaci ladění služby SharePoint
 K tomuto problému dochází, pokud nastavíte zarážku v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení služby SharePoint, stisknete klávesu **F5** pro spuštění a pak zůstanete na zarážce delší než 90 sekund.

### <a name="error-message"></a>Chybová zpráva
 Proces webového serveru, který se právě ladí, byl ukončen Internetová informační služba (IIS). Tomuto problému se můžete vyhnout tak, že ve službě IIS nakonfigurujete nastavení nástroje pro odesílání do fondu aplikací. Další podrobnosti najdete v nápovědě.

### <a name="resolution"></a>Řešení
 Ve výchozím nastavení fond aplikací služby IIS počká 90 sekund, než aplikace odpoví před ukončením aplikace. Tento proces se označuje jako "použití příkazu" při testu. Chcete-li tento problém vyřešit, můžete buď prodloužit dobu čekání, nebo úplně zakázat příkaz pro odeslání aplikace.

##### <a name="to-access-the-iis-app-pool-settings"></a>Přístup k nastavení fondu aplikací služby IIS

1. Otevřete Správce služby IIS.

2. V podokně **připojení** rozbalte uzel server SharePoint a pak zvolte uzel **fondy aplikací** .

3. Na stránce **fondy aplikací** zvolte fond aplikací služby SharePoint (obvykle "SharePoint-80") a pak v podokně **Akce** zvolte odkaz **Rozšířená nastavení** .

4. Pokud chcete prodloužit dobu čekání před vypršením časového limitu služby IIS, změňte hodnotu **Maximální doba odezvy nástroje příkazového testu (sekundy)** na hodnotu, která je větší než 90 sekund.

5. Pokud chcete **zakázat příkaz pro zadání testu** služby IIS, nastavte na **hodnotu NEPRAVDA**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Automatické odvolání opustí instanci osamoceného seznamu ve službě SharePoint.
 K tomuto problému dochází, pokud provedete následující kroky.

1. Vytvoří definici seznamu, která má v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]instanci seznamu.

2. Kliknutím na klávesu **F5** spusťte řešení.

3. Zastavit ladění nebo zavřít web služby SharePoint.

4. Znovu otevřete web služby SharePoint a otevřete instanci seznamu.

### <a name="error-message"></a>Chybová zpráva
 Chyba serveru v aplikaci/

### <a name="resolution"></a>Řešení
 K tomu dochází, protože po zavření relace ladění řešení služby SharePoint, funkce automatického odčítání odvolá řešení. Odvolání odstraní definici seznamu ze SharePointu, ale neodstraní instanci tohoto seznamu. Základní definice seznamu je vyžadována instancí seznamu.

 Chcete-li tento problém vyřešit, nasaďte řešení v panelu nabídek a zvolte možnost **sestavit** > **nasadit**. (Neladit řešení volbou klávesy **F5** .) Pak odstraňte instanci seznamu na SharePointu.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Původní řešení služby SharePoint je nahrazeno exportovanou verzí.
 Pokud exportujete řešení služby SharePoint, importujte řešení do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]a pak řešení nasaďte zpátky na stejnou lokalitu, ze které byla exportována, původní řešení služby SharePoint bude nahrazeno. K tomuto problému nedojde, pokud řešení nasazujete na server, na kterém není aktivované původní řešení.

### <a name="error-message"></a>Chybová zpráva
 Žádné

### <a name="resolution"></a>Řešení
 Chcete-li se vyhnout přepsání řešení na webu, ze kterého byl exportován, změňte identifikátory GUID SolutionID a ID funkcí všech importovaných funkcí v projektu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="error-appears-when-debugging-starts"></a>Při zahájení ladění se zobrazí chyba.
 Když začnete ladit řešení služby SharePoint v aplikaci Visual Studio, chyba znamená, že Visual Studio nemůže načíst soubor Web. config, protože daný klíč není ve slovníku.

### <a name="error-message"></a>Chybová zpráva
 Nelze načíst konfigurační soubor Web. config. Ověřte soubor pro všechny poškozené prvky XML a zkuste to znovu. Došlo k následující chybě: daný klíč není ve slovníku přítomen.

### <a name="resolution"></a>Řešení
 Chcete-li vyřešit tento problém, ujistěte se, že hodnota vlastnosti Adresa URL webu projektu služby SharePoint v aplikaci Visual Studio odpovídá adrese URL, která je přiřazena výchozí zóně pro mapování alternativního přístupu pro webovou aplikaci. Tuto chybu nelze vyřešit pomocí jiné zóny, jako je například intranet, pro adresu URL. Adresa URL webu projektu a adresa URL ve výchozí zóně se musí shodovat. Chcete-li získat přístup k mapování alternativního přístupu, otevřete nástroj centrální správy služby SharePoint 2010, zvolte odkaz **Správa aplikací** a potom v části **webové aplikace**zvolte odkaz **Konfigurovat mapování alternativního přístupu** . Další informace najdete v tématu [vytvoření zón pro webové aplikace](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Viz také:

- [Řešení potíží s balením a nasazením služby SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)