---
title: Položky registru pro doplňky VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 14d35e8d6aa6209f628e38be65c9be5fbc614561
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673013"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Položky registru pro doplňky VSTO
  Při nasazení doplňků VSTO, které jsou vytvořené pomocí sady Visual Studio, musíte vytvořit konkrétní sady položek registru. Tyto položky registru poskytují informace, které umožní aplikaci Microsoft Office zjišťovat a načíst doplňku VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Při sestavování projektu sady Visual Studio vytvoří tyto položky registru na vývojovém počítači, takže můžete snadno spouštět a ladit doplňku VSTO. Pokud nasazení doplňku VSTO pomocí ClickOnce, jsou automaticky vytvořeny položky registru v počítači koncového uživatele. Pokud nasazení doplňku VSTO pomocí Instalační služby systému Windows, musíte nakonfigurovat projekt InstallShield Limited Edition vytvořit položky registru v počítači koncového uživatele.  
  
 Další informace o tom, jak použít položky registru během procesu načtení pro doplňky VSTO najdete v tématu [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  V tomto tématu se text *ID doplňku* představuje jedinečné ID pro váš doplněk VSTO. Ve výchozím nastavení ID je název vašeho sestavení doplňku VSTO.  
  
## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrace doplňků VSTO pro aktuálního uživatele a všichni uživatelé  
 Když doplňku VSTO je nainstalována, lze jej zaregistrovat dvěma způsoby:  
  
- Pro aktuálního uživatele (to znamená, je dostupná jenom pro uživatele, který je přihlášen k počítači při instalaci doplňku VSTO). V takovém případě položky registru jsou vytvořeny v rámci **HKEY_CURRENT_USER**.  
  
- Pro všechny uživatele (každý uživatel, který se přihlásí k počítači, můžete použít doplňku VSTO). V takovém případě položky registru jsou vytvořeny v rámci **HKEY_LOCAL_MACHINE**.  
  
  Všechny doplňků VSTO, které vytvoříte pomocí sady Visual Studio lze zaregistrovat pro aktuálního uživatele. Doplňky VSTO však lze zaregistrovat pro všechny uživatele v určitých scénářích. Těchto scénářů závisí na verzi Microsoft Office v počítači a způsobu nasazení doplňku VSTO.  
  
### <a name="microsoft-office-version"></a>Verze aplikace Microsoft Office  
 Aplikace Office může načíst doplňků VSTO, které jsou registrovány v rámci **HKEY_LOCAL_MACHINE** nebo **HKEY_CURRENT_USER**.  
  
 Načtení doplňků VSTO, které jsou registrovány v rámci **HKEY_LOCAL_MACHINE**, počítačích musí být balíček aktualizace 976477 nainstalované. Další informace najdete na webu [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### <a name="deployment-type"></a>Typ nasazení  
 Pokud nasazení doplňku VSTO pomocí ClickOnce, doplňku VSTO lze zaregistrovat pouze pro aktuálního uživatele. Důvodem je, že ClickOnce podporuje pouze vytváření klíčů v rámci **HKEY_CURRENT_USER**. Pokud chcete zaregistrovat doplňku VSTO pro všechny uživatele v počítači, musíte použít instalační služby systému Windows k nasazení doplňku VSTO. Další informace o těchto typech nasazení najdete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) a [nasazení řešení Office s použitím Instalační služby systému Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="registry-entries"></a>Položky registru  
 Požadované položky registru doplňku VSTO jsou umístěny v následujícím klíči registru pro všechny aplikace s výjimkou Visio, kde *kořenové* je **HKEY_CURRENT_USER** nebo **HKEY_LOCAL_MACHINE** .  
  
 **Všechny aplikace s výjimkou aplikace Visio**  
  
|Verze Office|Konfigurační cesta|  
|--------------------|------------------------|  
|32bitová|*Kořenové*\Software\Microsoft\Office\\*název_aplikace*\Addins\\*ID doplňku*|  
|64bitových|*Kořenové*\Software\Wow6432Node\Microsoft\Office\\*název_aplikace*\Addins\\*ID doplňku*|  
  
 **Aplikace Visio**  
  
|Verze Office|Konfigurační cesta|  
|--------------------|------------------------|  
|32bitová|*Kořenové*\Software\Microsoft\Visio\Addins\\*ID doplňku*|  
|64bitových|*Kořenové*\Software\Wow6432Node\Visio\Addins\\*ID doplňku*|  
  
 V následující tabulce jsou uvedeny položky v tomto klíči registru.  
  
|Položka|Typ|Hodnota|  
|-----------|----------|-----------|  
|**Popis**|REG_SZ|Požadováno. Stručný popis doplňku VSTO.<br /><br /> Tento popis se zobrazí, když uživatel vybere doplňku VSTO v **Add-Ins** podokně **možnosti** dialogové okno v aplikaci Microsoft Office.|  
|**FriendlyName**|REG_SZ|Požadováno. Popisný název VSTO doplněk, který se zobrazí v **doplňky modelu COM** dialogové okno v aplikaci Microsoft Office. Výchozí hodnota je ID doplňku VSTO|  
|**LoadBehavior**|REG_DWORD|Požadováno. Hodnota, která určuje, kdy se aplikace pokusí načíst doplňku VSTO a aktuální stav doplňku VSTO (načteny nebo uvolněny).<br /><br /> Tato položka je standardně nastavenou hodnotu 3, která určuje, že doplňku VSTO je načten při spuštění. Další informace najdete v tématu [hodnotách LoadBehavior](#LoadBehavior). **Poznámka:** Pokud uživatel zakáže doplňku VSTO, tato akce změní **LoadBehavior** hodnotu **HKEY_CURRENT_USER** podregistr registru. Pro každého uživatele, hodnota **LoadBehavior** přepíše výchozí hodnoty v podregistru HKEY_CURRENT_USER **LoadBehavior** definované v **HKEY_LOCAL_MACHINE** hive.|  
|**Manifest**|REG_SZ|Požadováno. Úplná cesta manifest nasazení pro doplňku VSTO. Cesta může být umístění na místním počítači sdílen v síti (UNC) nebo webového serveru (HTTP).<br /><br /> Pokud nasazení řešení pomocí Instalační služby systému Windows, je nutné přidat předponu **file:///** k **manifestu** cestu. Musíte také připojte řetězec  **&#124;vstolocal** (to znamená, znakem svislé čáry **&#124;** následovaný **vstolocal**) na konec této cesty. Tím se zajistí, že vaše řešení se načte z instalační složky, nikoli z mezipaměti ClickOnce. Další informace najdete v tématu [nasazení řešení Office s použitím Instalační služby systému Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Poznámka:** při vytvoření doplňku VSTO ve vývojovém počítači Visual Studio automaticky přidá  **&#124;vstolocal** řetězec, který má tato položka registru.|  
  
###  <a name="OutlookEntries"></a> Položky registru pro oblasti formuláře Outlooku  
 Pokud vytvoříte vlastní formulář regionu v doplňku VSTO pro Outlook, další registru položky se používají k registraci oblasti formuláře aplikace Outlook. Tyto položky jsou vytvářeny pod klíčem registru pro každou třídu zpráv, který podporuje oblasti formuláře. Tyto klíče registru jsou v následujícím umístění, kde *kořenové* je **HKEY_CURRENT_USER** nebo **HKEY_LOCAL_MACHINE**.  
  
 *Kořenové*\Software\Microsoft\Office\Outlook\FormRegions\\*message – třída*  
  
 Stejně jako jiné položky registru sdílí všechny doplňky VSTO, Visual Studio vytvoří formuláři položky registru oblast na vývojovém počítači při sestavování projektu. Pokud nasazení doplňku VSTO pomocí ClickOnce, jsou automaticky vytvořeny položky registru v počítači koncového uživatele. Pokud nasazení doplňku VSTO pomocí Instalační služby systému Windows, musíte nakonfigurovat projekt InstallShield Limited Edition vytvořit položky registru v počítači koncového uživatele.  
  
 Další informace o položkách registru oblasti formuláře, naleznete v tématu [umístění oblasti formuláře ve formě vlastních](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Další informace o oblastech formulářů aplikace Outlook, naleznete v tématu [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> Hodnotách LoadBehavior  
 **LoadBehavior** položku *kořenové*\Software\Microsoft\Office\\*název_aplikace*\Addins\\ *– doplněk ID* klíč obsahuje bitová kombinace hodnot, které určují chování běhu v doplňku VSTO. Nejnižší bitem (hodnoty 0 a 1) označuje, zda doplňku VSTO je aktuálně uvolněných nebo načtena. Ostatní bity o tom, kdy se aplikace pokusí načíst doplňku VSTO.  
  
 Obvykle **LoadBehavior** položka má být nastaveno na 0, 3 nebo 16 (v desítkové soustavě) při doplňku VSTO instalaci v počítačích koncových uživatelů. Ve výchozím nastavení, aplikace Visual Studio nastaví **LoadBehavior** položky z vašeho doplňku VSTO pro 3 při sestavení nebo ji publikovat.  
  
 V následující tabulce jsou uvedeny všechny možné hodnoty **LoadBehavior** položka. Některé popisy v této tabulce najdete načítání doplňku VSTO ručně nebo prostřednictvím kódu programu. Načtení doplňku VSTO ručně, zaškrtněte políčko vedle doplňku VSTO v **doplňky modelu COM** dialogové okno v aplikaci. Načtení doplňku VSTO prostřednictvím kódu programu, nastavte <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> vlastnost <xref:Microsoft.Office.Core.COMAddIn> objekt, který reprezentuje doplňku VSTO pro **true**.  
  
|Hodnota (v desítkové soustavě)|Stav doplňku VSTO|Chování zatížení doplňku VSTO|Popis|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|Není načten|Nenačítat automaticky|Aplikace se nikdy pokusí automaticky načte doplňku VSTO. Uživatel můžete zkusit ruční načtení doplňku VSTO nebo doplňku VSTO lze načíst prostřednictvím kódu programu.<br /><br /> Pokud doplňku VSTO je úspěšně načtena, **LoadBehavior** hodnoty 0 zůstane, ale stav doplňku VSTO v **doplňky modelu COM** dialogové okno se aktualizuje k označení, že doplňku VSTO je načtena.|  
|1|Načten|Nenačítat automaticky|Aplikace se nikdy pokusí automaticky načte doplňku VSTO. Uživatel můžete zkusit ruční načtení doplňku VSTO nebo doplňku VSTO lze načíst prostřednictvím kódu programu.<br /><br /> I když **doplňky modelu COM** dialogovému oknu označuje, že doplňku VSTO je načtena po spuštění aplikace doplňku VSTO není načteny, dokud je načten ručně nebo prostřednictvím kódu programu.<br /><br /> Pokud se aplikace úspěšně načte doplňku VSTO, **LoadBehavior** hodnota se změní na hodnotu 0 a po zavření aplikace zůstává na 0.|  
|2|Není načten|Načíst při spuštění|Aplikace se nepokusí se automaticky načte doplňku VSTO. Uživatel můžete zkusit ruční načtení doplňku VSTO nebo doplňku VSTO lze načíst prostřednictvím kódu programu.<br /><br /> Pokud se aplikace úspěšně načte doplňku VSTO, **LoadBehavior** hodnota se změní na 3 a zůstává na 3 po zavření aplikace.|  
|3|Načten|Načíst při spuštění|Aplikace se pokusí načíst doplňku VSTO při spuštění aplikace. Toto je výchozí hodnota při sestavení nebo publikování doplňku VSTO v sadě Visual Studio.<br /><br /> Pokud se aplikace úspěšně načte doplňku VSTO, **LoadBehavior** hodnota zůstane 3. Pokud dojde k chybě při načítání doplňku VSTO, **LoadBehavior** hodnota se změní na 2 a zůstává na 2 po zavření aplikace.|  
|8|Není načten|Načíst na požádání|Aplikace se nepokusí se automaticky načte doplňku VSTO. Uživatel můžete zkusit ruční načtení doplňku VSTO nebo doplňku VSTO lze načíst prostřednictvím kódu programu.<br /><br /> Pokud se aplikace úspěšně načte doplňku VSTO, **LoadBehavior** hodnota nezmění na 9.|  
|9|Načten|Načíst na požádání|Doplněk VSTO načtou pouze v případě, že aplikace vyžaduje, například když uživatel klikne prvek uživatelského rozhraní, která používá funkci VSTO Add-in (například vlastní tlačítko na pásu karet).<br /><br /> Pokud se aplikace úspěšně načte doplňku VSTO, **LoadBehavior** hodnota zůstane 9, ale stav doplňku VSTO v **doplňky modelu COM** dialogové okno se aktualizuje označuje, že doplňku VSTO aktuálně načtené. Pokud dojde k chybě při načítání doplňku VSTO, **LoadBehavior** hodnota nezmění na 8.|  
|16|Načten|Při prvním načtení a pak nahrajte na vyžádání|Nastavte tuto hodnotu, pokud chcete, aby vaše doplňku VSTO pro načtení na požádání. Když uživatel spustí aplikaci poprvé, načtení aplikace doplňku VSTO. Při příštím spuštění aplikace, aplikace načte všechny prvky uživatelského rozhraní, které jsou definovány v doplňku VSTO, ale doplňku VSTO není načten, dokud uživatel neklikne prvku uživatelského rozhraní, který je přidružený k doplňku VSTO.<br /><br /> Při úspěšném načtení aplikace doplňku VSTO pro první spuštění **LoadBehavior** hodnota zůstane 16 při načtení doplňku VSTO. Po zavření aplikace **LoadBehavior** hodnota nezmění na 9.|  
  
## <a name="see-also"></a>Viz také:  
 [Architektura řešení pro Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
  