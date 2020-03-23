---
title: Položky registru pro doplňky VSTO
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416520"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Položky registru pro doplňky VSTO
  Při nasazování doplňků VSTO vytvořených pomocí sady Visual Studio je nutné vytvořit určitou sadu položek registru. Tyto položky registru poskytují informace, které umožňují aplikaci Sady Microsoft Office zjistit a načíst doplněk VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Při vytváření projektu visual studio vytvoří tyto položky registru ve vývojovém počítači, takže můžete snadno spustit a ladit Doplněk VSTO. Pokud použijete ClickOnce k nasazení doplňku VSTO, položky registru se automaticky vytvoří v počítači koncového uživatele. Pokud k nasazení doplňku VSTO používáte Instalační službu systému Windows, je nutné nakonfigurovat projekt Limitované edice InstallShield a vytvořit položky registru v počítači koncového uživatele.

 Další informace o tom, jak jsou položky registru používány během procesu načítání doplňků VSTO, naleznete v [tématu Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> V tomto tématu představuje *ID doplňku* textu jedinečné ID doplňku VSTO. Ve výchozím nastavení je ID název sestavení doplňku VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrace doplňků VSTO pro aktuálního uživatele vs. všechny uživatele
 Když je doplněk VSTO nainstalován, lze jej zaregistrovat dvěma způsoby:

- Pouze pro aktuálního uživatele (to znamená, že je k dispozici pouze uživateli, který je přihlášen k počítači při instalaci doplňku VSTO). V tomto případě jsou položky registru vytvořeny pod **HKEY_CURRENT_USER**.

- Pro všechny uživatele (to znamená, že každý uživatel, který se přihlásí k počítači, může použít doplněk VSTO). V tomto případě jsou položky registru vytvořeny pod **HKEY_LOCAL_MACHINE**.

  Všechny doplňky VSTO, které vytvoříte pomocí sady Visual Studio, lze zaregistrovat pro aktuálního uživatele. Doplňky VSTO však lze zaregistrovat pro všechny uživatele pouze v určitých scénářích. Tyto scénáře závisí na verzi sady Microsoft Office v počítači a na tom, jak byl doplněk VSTO nasazen.

### <a name="deployment-type"></a>Typ nasazení
 Pokud použijete ClickOnce k nasazení doplňku VSTO, doplněk VSTO lze zaregistrovat pouze pro aktuálního uživatele. Důvodem je, že ClickOnce podporuje pouze vytváření klíčů pod **HKEY_CURRENT_USER**. Pokud chcete zaregistrovat doplněk VSTO pro všechny uživatele v počítači, musíte použít Instalační službu systému Windows k nasazení doplňku VSTO. Další informace o těchto typech nasazení najdete [v tématu Nasazení řešení Office pomocí clickonce](../vsto/deploying-an-office-solution-by-using-clickonce.md) a [nasazení řešení Office pomocí Instalační služby systému Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Položky registru
 Požadované položky registru doplňku VSTO jsou umístěny pod následujícími klíči registru, kde je *kořenová* **HKEY_CURRENT_USER** nebo **HKEY_LOCAL_MACHINE** v závislosti na tom, zda je instalace pro aktuálního uživatele nebo všechny uživatele.

|Aplikace Office|Cesta konfigurace|
|------------------|------------------|
|Visio|*Kořen*\\\Software\ID*doplňku* Aplikace\\Microsoft*Visio*\Addins|
|Všechny ostatní|*Kořenový*adresář \Software\Microsoft\Název\\*aplikace sady Office*\Addins\\*ID doplňku*|

> [!NOTE]
> Pokud instalační program cílí na všechny uživatele v 64bitovém systému Windows, doporučuje se, aby zahrnoval dvě\\položky registru, jednu pod HKEY_LOCAL_MACHINE\Software\Microsoft a jednu pod HKEY_LOCAL_MACHINE\Software**WOW6432Node**\Microsoft hive. Je to proto, že uživatelé mohou v počítači používat 32bitové nebo 64bitové verze sady Office.
>
>Pokud instalační program cílí na aktuálního uživatele, není nutné jej instalovat do uzlu WOW6432Node, protože je sdílena cesta HKEY_CURRENT_USER\Software.
>
>Další informace naleznete [v části 32bitová a 64bitová data aplikací v registru](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 V následující tabulce jsou uvedeny položky pod tímto klíčem registru.

|Záznam|Typ|Hodnota|
|-----------|----------|-----------|
|**Popis**|REG_SZ|Povinná hodnota. Stručný popis doplňku VSTO.<br /><br /> Tento popis se zobrazí, když uživatel vybere doplněk VSTO v podokně **doplňků** dialogového okna **Možnosti** v aplikaci Microsoft Office.|
|**Friendlyname**|REG_SZ|Povinná hodnota. Popisný název doplňku VSTO, který se zobrazí v dialogovém okně **Doplňky com** v aplikaci sady Microsoft Office. Výchozí hodnota je ID doplňku VSTO.|
|**LoadBehavior**|REG_DWORD|Povinná hodnota. Hodnota, která určuje, kdy se aplikace pokusí načíst doplněk VSTO a aktuální stav doplňku VSTO (načtený nebo nezatížený).<br /><br /> Ve výchozím nastavení je tato položka nastavena na hodnotu 3, což určuje, že doplněk VSTO je načten při spuštění. Další informace naleznete v tématu [LoadBehavior hodnoty](#LoadBehavior). **Poznámka:**  Pokud uživatel zakáže doplněk VSTO, tato akce upraví **hodnotu LoadBehavior** v podregistru **HKEY_CURRENT_USER** registru. Pro každého uživatele hodnota **LoadBehavior** v podregistru HKEY_CURRENT_USER přepíše výchozí **LoadBehavior** definované v **podregistru HKEY_LOCAL_MACHINE.**|
|**Manifest**|REG_SZ|Povinná hodnota. Úplná cesta manifestu nasazení pro doplněk VSTO. Cesta může být umístění v místním počítači, sdílená síť (UNC) nebo webový server (HTTP).<br /><br /> Pokud k nasazení řešení použijete Instalační službu systému Windows, je nutné přidat předponu **file:///** do cesty **manifestu.** Musíte také připojit řetězec **&#124;vstolocal** (to znamená znak kanálu **&#124;** následovaný **vstolocal**) na konec této cesty. Tím zajistíte, že vaše řešení je načten z instalační složky, nikoli clickonce mezipaměti. Další informace naleznete [v tématu Deploy an Office solution using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md). **Poznámka:**  Při vytváření doplňku VSTO ve vývojovém počítači visual studio automaticky připojí **&#124;vstolocal** řetězec k této položce registru.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Položky registru pro oblasti formuláře aplikace Outlook
 Pokud vytvoříte vlastní oblast formuláře v doplňku VSTO pro aplikaci Outlook, budou další položky registru použity k registraci oblasti formuláře v aplikaci Outlook. Tyto položky jsou vytvořeny pod jiným klíčem registru pro každou třídu zprávy, kterou oblast formuláře podporuje. Tyto klíče registru jsou v následujícím umístění, kde *je kořen* **ováHKEY_CURRENT_USER** nebo **HKEY_LOCAL_MACHINE**.

 *Kořenová*třída\\*zprávy* Root\Software\Microsoft\Office\Outlook\FormRegions

 Stejně jako ostatní položky registru sdílené všemi doplňky VSTO, Visual Studio vytvoří položky registru oblasti formuláře ve vývojovém počítači při vytváření projektu. Pokud použijete ClickOnce k nasazení doplňku VSTO, položky registru se automaticky vytvoří v počítači koncového uživatele. Pokud k nasazení doplňku VSTO používáte Instalační službu systému Windows, je nutné nakonfigurovat projekt Limitované edice InstallShield a vytvořit položky registru v počítači koncového uživatele.

 Další informace o položkách registru oblasti formuláře naleznete [v tématu Určení umístění oblasti formuláře ve vlastním formuláři](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Další informace o oblastech formulářů aplikace Outlook naleznete v [tématu Vytvoření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a>Hodnoty LoadBehavior
 Položka **LoadBehavior** pod *kořenovým*\Software\Microsoft\Název\\*aplikace*\\Sady \Addins*obsahuje* bitovou kombinaci hodnot, které určují chování doplňku VSTO při běhu. Nejnižší bit objednávky (hodnoty 0 a 1) označuje, zda je doplněk VSTO aktuálně uvolněn nebo načten. Jiné bity označují, když se aplikace pokusí načíst doplněk VSTO.

 Položka **LoadBehavior** je obvykle určena k nastavení na 0, 3 nebo 16 (v desítkové min. v desítkové mlze), pokud je doplněk VSTO nainstalován v počítačích koncových uživatelů. Ve výchozím nastavení Visual Studio nastaví položku **LoadBehavior** doplňku VSTO na 3 při jeho sestavení nebo publikování.

 V následující tabulce jsou uvedeny všechny možné hodnoty položky **LoadBehavior.** Některé popisy v této tabulce odkazují na ruční nebo programové načítání doplňku VSTO. Chcete-li doplněk VSTO načíst ručně, zaškrtněte políčko vedle doplňku VSTO v dialogovém okně **Doplňky com** v aplikaci. Chcete-li doplněk VSTO načíst programově, <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> nastavte <xref:Microsoft.Office.Core.COMAddIn> vlastnost objektu, který představuje doplněk VSTO, na **hodnotu true**.

|Hodnota (v desítkové min. desítce)|Stav doplňku VSTO|Chování načtení doplňku VSTO|Popis|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|uvolněné|Nenačítat automaticky|Aplikace se nikdy nepokusí automaticky načíst doplněk VSTO. Uživatel se může pokusit ručně načíst doplněk VSTO nebo doplněk VSTO lze načíst programově.<br /><br /> Pokud je doplněk VSTO úspěšně načten, hodnota **LoadBehavior** zůstane 0, ale stav doplňku VSTO v dialogovém okně **Doplňky com** je aktualizován, aby bylo zřejmé, že doplněk VSTO je načten.|
|1|Načten|Nenačítat automaticky|Aplikace se nikdy nepokusí automaticky načíst doplněk VSTO. Uživatel se může pokusit ručně načíst doplněk VSTO nebo doplněk VSTO lze načíst programově.<br /><br /> Přestože dialogové okno **Doplňky com** označuje, že doplněk VSTO je načten po spuštění aplikace, doplněk VSTO není načten, dokud není načten ručně nebo programově.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** se změní na hodnotu 0 a zůstane na hodnotě 0 po ukončení aplikace.|
|2|uvolněné|Načíst při spuštění|Aplikace se nepokouší načíst doplněk VSTO automaticky. Uživatel se může pokusit ručně načíst doplněk VSTO nebo doplněk VSTO lze načíst programově.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** se změní na 3 a zůstane na 3 po ukončení aplikace.|
|3|Načten|Načíst při spuštění|Aplikace se pokusí načíst doplněk VSTO při spuštění aplikace. Toto je výchozí hodnota při vytváření nebo publikování doplňku VSTO v sadě Visual Studio.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** zůstane 3. Pokud dojde k chybě při načítání doplňku VSTO, hodnota **LoadBehavior** se změní na 2 a zůstane na 2 po ukončení aplikace.|
|8|uvolněné|Zatížení na vyžádání|Aplikace se nepokouší načíst doplněk VSTO automaticky. Uživatel se může pokusit ručně načíst doplněk VSTO nebo doplněk VSTO lze načíst programově.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** se změní na hodnotu 9.|
|9|Načten|Zatížení na vyžádání|Doplněk VSTO se načte pouze v případě, že to aplikace vyžaduje, například když uživatel klepne na prvek uživatelského rozhraní, který používá funkce v doplňku VSTO (například vlastní tlačítko na pásu karet).<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** zůstane 9, ale stav doplňku VSTO v dialogovém okně **Doplňky com** je aktualizován, aby bylo zřejmé, že doplněk VSTO je aktuálně načten. Pokud dojde k chybě při načítání doplňku VSTO, hodnota **LoadBehavior** se změní na 8.|
|16|Načten|Načíst první čas, pak zatížení na vyžádání|Tuto hodnotu nastavte, pokud chcete, aby byl doplněk VSTO načten na vyžádání. Aplikace načte doplněk VSTO při prvním spuštění aplikace uživatelem. Při příštím spuštění aplikace aplikace načte všechny prvky uživatelského rozhraní, které jsou definovány v doplňku VSTO, ale doplněk VSTO není načten, dokud uživatel neklepne na prvek uživatelského rozhraní, který je přidružen k doplňku VSTO.<br /><br /> Když aplikace úspěšně načte doplněk VSTO poprvé, **loadbehavior** hodnota zůstane 16, zatímco doplněk VSTO je načten. Po ukončení aplikace se hodnota **LoadBehavior** změní na hodnotu 9.|

## <a name="see-also"></a>Viz také
- [Architektura řešení Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Vytváření řešení Office](../vsto/building-office-solutions.md)
- [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)
 