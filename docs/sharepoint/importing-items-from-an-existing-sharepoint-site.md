---
title: Import položek z existujícího webu služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c2703bfdd4f47281a1fc19060cb69f8b312e7d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017026"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Import položek z existujícího webu služby SharePoint
  Šablona projektu importovat balíček řešení služby SharePoint umožňuje znovu použít prvky, jako jsou typy obsahu a pole z existujících webů služby SharePoint v novém [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení služby SharePoint. I když lze spustit většinu importovaných řešení bez úprav, existují určitá omezení a problémy, které je třeba zvážit, zejména pokud po importu změníte jakékoli položky.

> [!NOTE]
> K importu opakovaně použitelných pracovních postupů použijte šablonu projektu importovat opakovaně použitelnou pracovní postup. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Pokyny pro import opakovaně použitelných pracovních postupů](../sharepoint/guidelines-for-importing-reusable-workflows.md).

## <a name="supported-sharepoint-solutions"></a>Podporovaná řešení služby SharePoint
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] plně podporuje import řešení vytvořených v [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] a [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] nepodporuje import řešení vytvořených v následujících aplikacích:

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  I když můžete často úspěšně importovat řešení vytvořená těmito aplikacemi, tato funkce není testována a není podporována.

## <a name="item-import-restrictions"></a>Omezení importu položek
 I když většinu položek služby SharePoint lze importovat z existujícího souboru *WSP* , následující položky nejsou podporovány a mohou vyžadovat správné fungování úprav:

- Entity služby BDC

- Prvky přidružení pracovního postupu kódu

- Pracovní postupy kódu

- Vizuální webové části (. ascx)

- Webové služby (*. asmx*)

- Vazby typu obsahu

- Přijímače událostí

- Seznam definic (šablon)

- Definice webu

  Když vyexportujete řešení z [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , tyto položky budou automaticky vyloučeny ze souboru *. wsp* . Nicméně jiné soubory *. wsp* vygenerované z nepodporovaných nástrojů můžou tyto položky obsahovat. (Další informace najdete v části podporovaná řešení služby SharePoint výše v tomto tématu.)

## <a name="what-happens-when-you-import-a-solution"></a>Co se stane po importu řešení
 Když importujete řešení se šablonou balíčku řešení služby SharePoint, nástroj [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zkopíruje celý obsah souboru *. wsp* a pokusí se sjednotit a zachovat tolik přidružení a jejich odkazů mezi importovanými prvky a jejich soubory.

 Všechny importované položky se zkopírují do odpovídajících složek v **Průzkumník řešení**. Například typy obsahu se zobrazí v části **typy obsahu** složky a instance seznamu se zobrazí v části **instance seznamu**. Soubory přidružené k importované položce jsou zkopírovány také do složky položky. Například instance importovaného seznamu obsahuje své moduly, formuláře a stránky ASPX.

### <a name="dependent-items"></a>Závislé položky
 Pokud vyberete položku v Průvodci importem balíčku řešení služby SharePoint, ale ne jako její závislé položky, zobrazí se v okně se zprávou, že před importem musí být také vybrána možnost závislé položky.

### <a name="what-are-features"></a>Co jsou funkce?
 Uživatelé návrháře SharePointu můžou v importovaných řešeních v Průzkumník řešení zobrazit neočekávané soubory, které se nazývají *funkce* **.** I když v řešení SharePoint Designer existovaly funkce, jsou skryté ze zobrazení. Funkce jsou nyní viditelné v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Funkce jsou kontejnery pro položky SharePointu. Každá funkce udržuje odkaz na každou položku, jako jsou typy obsahu a definice seznamů, které obsahuje. Při importu řešení aplikace [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nastaví funkce pro všechny importované prvky a pokusy o udržování vztahů mezi prvky pro soubory. Všechny soubory, jejichž odkazy nemohly být přeloženy, jsou umístěny do složky **ostatní importované soubory** .

 Další informace o funkcích naleznete v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md) a [práce s funkcemi](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Zpracování speciálních případů
 V některých případech aplikace Visual Studio nemůže sjednotit položku se závislými soubory. Všechny soubory, které se [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nedají přeložit, se zobrazí ve složce **jiné importované soubory**. Kromě toho jejich vlastnosti **typ nasazení** jsou nastaveny na **Nenasazení** tak, aby nebyly nasazeny s řešením.

 Pokud například importujete seznam ExpenseForms, definice seznamu s tímto názvem se zobrazí ve složce **definice seznamu** v **Průzkumník řešení** společně se soubory *Elements.xml* a *Schema.xml* . Přidružené formuláře ASPX a HTML ale mohou být umístěny do složky s názvem **ExpenseForms** ve složce **ostatní importované soubory** . Chcete-li dokončit import, přesuňte tyto soubory pod definicí seznamu ExpenseForms v **Průzkumník řešení** a změňte vlastnost **typ nasazení** pro každý soubor z **nasazení** na **ElementFile**.

 Při importu přijímačů událostí je soubor *Elements.xml* zkopírován do správného umístění, ale je nutné ručně zahrnout sestavení do balíčku řešení, aby se nasadilo do řešení. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] Postup najdete v tématu [Postup: Přidání a odebrání dalších sestavení](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Při importu pracovních postupů se formuláře InfoPathu zkopírují do složky **ostatní importované soubory** . Pokud soubor *. wsp* obsahuje webovou šablonu, je nastaven jako úvodní stránka v **Průzkumník řešení**.

## <a name="import-fields-and-property-bags"></a>Importovat pole a penalty vlastností
 Při importu řešení, které obsahuje více polí, jsou všechny definice samostatných polí sloučeny do jednoho *Elements.xml* souboru pod uzlem v **Průzkumník řešení** s názvem **pole**. Podobně všechny položky kontejneru objektů a dat jsou sloučeny do souboru *Elements.xml* pod uzlem s názvem **PropertyBags**.

 Pole v SharePointu jsou sloupce zadaného datového typu, jako je například text, logická hodnota nebo vyhledávání. Další informace naleznete v tématu [stavební blok: sloupce a typy polí](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). Kontejnery objektů a služeb umožňují přidat vlastnosti do objektů ve službě SharePoint, vše z farmy do seznamu na webu služby SharePoint. Kontejnery objektů a dat jsou implementovány jako zatřiďovací tabulka názvů vlastností a hodnot. Další informace najdete v tématu [Správa nastavení služby SharePoint](/previous-versions/msp-n-p/ff647766(v=pandp.10)) nebo [kontejneru vlastností služby SharePoint](https://archive.codeplex.com/?p=pbs).

## <a name="delete-items-in-the-project"></a>Odstranit položky v projektu
 Většina položek v řešeních služby SharePoint má jednu nebo více závislých položek. Například instance seznamů závisí na typech obsahu a typech obsahu závisejících na polích. Po importu řešení služby SharePoint vás [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] neupozorní na případné problémy s odkazem, pokud odstraníte položku v řešení, ale ne její závislé položky, dokud se nepokusíte nasazení řešení. Pokud například importované řešení obsahuje instanci seznamu, která závisí na typu obsahu a odstraníte tento typ obsahu, může při nasazení dojít k chybě. K této chybě dojde, pokud na serveru SharePoint není závislá položka. Podobně platí, že pokud Odstraněná položka má také související kontejner objektů a dat, odstraňte tyto položky kontejneru vlastností ze souboru **PropertyBags** *Elements.xml* . Proto pokud z importovaného řešení odstraníte nějaké položky a dojde k chybám při nasazení, zkontrolujte, jestli je potřeba odstranit taky nějaké závislé položky.

## <a name="restore-missing-feature-attributes"></a>Obnovení chybějících atributů funkce
 Při importu řešení jsou některé volitelné atributy funkcí vynechány v importovaném manifestu funkce. Chcete-li tyto atributy obnovit v novém souboru funkce, Identifikujte chybějící atributy porovnáním původního souboru funkce s novým manifestem funkce a postupujte podle pokynů v tématu [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>V předdefinovaných instancích seznamů se neprovádí zjišťování konfliktů nasazení.
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] neprovádí zjišťování konfliktů nasazení na předdefinovaných instancích seznamů (tj. výchozí instance seznamů, které jsou součástí služby SharePoint). Není prováděno zjišťování konfliktů, aby nedošlo k přepsání předdefinovaných instancí seznamu na SharePointu. Předdefinované instance seznamu jsou pořád nasazené nebo aktualizované, ale nikdy se neodstraňují ani nepřepíší. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Řešení potíží s balením a nasazením služby SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)

## <a name="import-sharepoint-server-2010-workflows"></a>Importovat pracovní postupy pro SharePoint Server 2010
 Pokud importujete pracovní postup vytvořený v nástroji [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , po jeho nasazení nebude správně fungovat. Pracovní postup neběží správně, protože chybí některá sestavení a  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] pracovní postupy obsahují formuláře InfoPathu, které se v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] řešení pracovních postupů aktuálně nepodporují. Importované [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] pracovní postupy však lze správně pracovat po opravě některých položek, jako je například přidání odkazů do [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] sestavení a opětovné připojení formulářů aplikace InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Importují se pracovní postupy pro SharePoint Server 2010](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Limit znaků názvu položky
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] má limit 260 znaků pro názvy položek projektu a projektu, včetně cesty. Pokud při importu řešení dojde k překročení tohoto limitu, zobrazí se chyba:

 **Zadaná cesta, název souboru nebo obojí jsou příliš dlouhé. Plně kvalifikovaný název souboru musí být kratší než 260 znaků a název adresáře musí být kratší než 248 znaků.**

 Když se zobrazí tato chyba, položka se nevytvoří. K tomuto problému dochází nejčastěji u importovaných modulů. Chcete-li se tomuto problému vyhnout, postupujte následovně:

- Použijte krátké názvy pro projekt, když je zadáte v dialogovém okně **Přidat nový projekt** .

- Vytvořte projekt v umístění co nejblíže kořenové složce, abyste mohli zkrátit cestu.

## <a name="the-sharepointproductversion-attribute"></a>Atribut SharePointProductVersion
 Pokud importujete řešení vytvořené v dřívější verzi služby SharePoint, například [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] nebo [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] , buď změňte hodnotu atributu SharePointProductVersion v manifestu balíčku na 12,0, nebo vložte ovládací prvek Správce skriptů do všech importovaných webových stránek a nechte SharePointProductVersion nastavenou na 14,0. V opačném případě se importované webové formuláře nezobrazí na SharePointu.

### <a name="background"></a>Pozadí
 Řešení v [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] a [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] zahrnují atribut s názvem SharePointProductVersion. SharePoint používá tento atribut v manifestech balíčku k určení verze SharePointu, pro kterou je řešení navržené. Tyto dvě platné hodnoty jsou 12,0 a 14,0. Hodnota 12,0 znamená, že položka je navržena pro [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] nebo [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] ; Hodnota 14,0 znamená, že je položka navržena pro [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 Pro zvýšení zabezpečení při vykreslování stránek ASPX [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] a [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] vyžadovat, aby všechny stránky ASPX nebo předlohy obsahovaly ovládací prvek Správce skriptů. Další informace o správci skriptů najdete v tématu [Přehled ovládacího prvku ScriptManager](/previous-versions/bb398863(v=vs.140)). Protože ovládací prvek Správce skriptů není k dispozici v [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] a [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] , musí být jeden přidán na [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] stránku nebo na [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] stránku, která je upgradována na [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] . Stránky ASPX, které používají standardní stránku předlohy, nevyžadují ovládací prvek Správce skriptů, protože jeden je již přidán na standardní stránku předlohy. Stránky ASPX, které nepoužívají stránku předlohy nebo které používají vlastní stránku předlohy, však musí přidat ovládací prvek skriptu, aby bylo možné pracovat v [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] nebo [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 Absence ovládacího prvku Správce skriptů může být problém při importu [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] nebo [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] projektu do [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , protože atribut SharePointProductVersion všech nových projektů je nastaven na 14,0. Pokud nasadíte upgradovaný projekt, který obsahuje webový formulář bez Správce skriptů, formulář se nezobrazí na SharePointu.

## <a name="see-also"></a>Viz také
- [Návod: import položek z existujícího webu služby SharePoint](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Pokyny pro import opakovaně použitelných pracovních postupů](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Návod: import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
