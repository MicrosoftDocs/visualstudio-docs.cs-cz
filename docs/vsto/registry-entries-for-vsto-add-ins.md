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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416520"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Položky registru pro doplňky VSTO
  Pokud nasazujete doplňky VSTO vytvořené pomocí sady Visual Studio, musíte vytvořit konkrétní sadu položek registru. Tyto položky registru obsahují informace, které umožní aplikaci systém Microsoft Office vyhledat a načíst doplněk VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Při sestavování projektu Visual Studio vytvoří tyto položky registru ve vývojovém počítači, aby bylo možné snadno spustit a ladit doplněk VSTO. Pokud použijete ClickOnce k nasazení doplňku VSTO, položky registru se automaticky vytvoří v počítači koncového uživatele. Pokud použijete Instalační služba systému Windows k nasazení doplňku VSTO, je nutné nakonfigurovat projekt InstallShield limit Edition tak, aby vytvořil položky registru v počítači koncového uživatele.

 Další informace o tom, jak se položky registru používají během procesu načítání pro doplňky VSTO, najdete v tématu [architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> V tomto tématu *ID doplňku* textu představuje jedinečné ID doplňku VSTO. Ve výchozím nastavení je toto ID název vašeho sestavení doplňku VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrovat doplňky VSTO pro aktuálního uživatele a všechny uživatele
 Když je doplněk VSTO nainstalovaný, dá se zaregistrovat dvěma způsoby:

- Pouze pro aktuálního uživatele (to znamená, že je k dispozici pouze pro uživatele, který je přihlášen k počítači při instalaci doplňku VSTO). V tomto případě se položky registru vytvoří pod **HKEY_CURRENT_USER**.

- Pro všechny uživatele (tj. libovolný uživatel, který se k počítači přihlašuje) může použít doplněk VSTO. V tomto případě se položky registru vytvoří v části **HKEY_LOCAL_MACHINE**.

  Všechny doplňky VSTO, které vytvoříte pomocí sady Visual Studio, můžete pro aktuálního uživatele zaregistrovat. Doplňky VSTO ale můžete zaregistrovat jenom pro všechny uživatele v určitých scénářích. Tyto scénáře závisí na verzi systém Microsoft Office v počítači a na způsobu nasazení doplňku VSTO.

### <a name="deployment-type"></a>Typ nasazení
 Pokud použijete ClickOnce k nasazení doplňku VSTO, doplněk VSTO se dá zaregistrovat jenom pro aktuálního uživatele. To je způsobeno tím, že ClickOnce podporuje pouze vytváření klíčů v rámci **HKEY_CURRENT_USER**. Pokud chcete zaregistrovat doplněk VSTO pro všechny uživatele v počítači, musíte k nasazení doplňku VSTO použít Instalační služba systému Windows. Další informace o těchto typech nasazení naleznete v tématu [nasazení řešení pro systém Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) a [nasazení řešení pro systém Office pomocí Instalační služba systému Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Položky registru
 Požadované položky registru doplňku VSTO jsou umístěné v následujících klíčích registru, kde se *kořen* **HKEY_CURRENT_USER** nebo **HKEY_LOCAL_MACHINE** v závislosti na tom, jestli je instalace pro aktuálního uživatele nebo pro všechny uživatele.

|Aplikace Office|Konfigurační cesta|
|------------------|------------------|
|Visio|*Root* \\ *Visio* \\ *ID doplňku* \Software\Microsoft Visia \Addins v kořenovém adresáři|
|Všechny ostatní|*Kořenová*\Software\Microsoft\Office \\ *název aplikace Office*\Addins \\ *– ID doplňku*|

> [!NOTE]
> Pokud instalační služba cílí na všechny uživatele v 64 Windows, doporučujeme, aby obsahovala dvě položky registru, jednu pod HKEY_LOCAL_MACHINE \Software\Microsoft a jednu v podregistru HKEY_LOCAL_MACHINE \Software \\ **Wow6432Node**\Microsoft. Důvodem je, že uživatelé můžou na počítači používat 32 nebo 64 bitové verze systému Office.
>
>Pokud instalační program cílí na aktuálního uživatele, není nutné ho instalovat do WOW6432Node, protože je sdílená cesta HKEY_CURRENT_USER \Software.
>
>Další informace najdete v části [32 a 64 data aplikace v registru](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry) .

 V následující tabulce jsou uvedeny položky v rámci tohoto klíče registru.

|Entry|Typ|Hodnota|
|-----------|----------|-----------|
|**Popis**|REG_SZ|Povinná hodnota. Stručný popis doplňku VSTO.<br /><br /> Tento popis se zobrazí, když uživatel vybere doplněk VSTO v podokně **Doplňky** v dialogovém okně **možnosti** v aplikaci systém Microsoft Office.|
|**FriendlyName**|REG_SZ|Povinná hodnota. Popisný název doplňku VSTO, který se zobrazí v dialogovém okně **Doplňky modelu COM** v aplikaci systém Microsoft Office. Výchozí hodnota je ID doplňku VSTO.|
|**LoadBehavior**|REG_DWORD|Povinná hodnota. Hodnota, která určuje, kdy se aplikace pokusí načíst doplněk VSTO a aktuální stav doplňku VSTO (načtený nebo uvolněný).<br /><br /> Ve výchozím nastavení je tato položka nastavená na hodnotu 3, která určuje, že doplněk VSTO se načte při spuštění. Další informace najdete v tématu [LoadBehavior Values](#LoadBehavior). **Poznámka:**  Pokud uživatel zakáže doplněk VSTO, tato akce upraví hodnotu **LoadBehavior** v podregistru **HKEY_CURRENT_USER** . U každého uživatele hodnota **LoadBehavior** v podregistru HKEY_CURRENT_USER přepisuje výchozí **LoadBehavior** definovaný v podregistru **HKEY_LOCAL_MACHINE** .|
|**Zřetel**|REG_SZ|Povinná hodnota. Úplná cesta k manifestu nasazení doplňku VSTO. Cesta může být umístění v místním počítači, sdílená síťová složka (UNC) nebo webový server (HTTP).<br /><br /> Použijete-li Instalační služba systému Windows k nasazení řešení, je nutné přidat předponu **File:///** do cesty k **manifestu** . Musíte také připojit řetězec **&#124;vstolocal** (to znamená, že znak kanálu **&#124;** následovaný parametrem **vstolocal**) na konec této cesty. Tím se zajistí, že se vaše řešení načte z instalační složky místo mezipaměti ClickOnce. Další informace najdete v tématu [nasazení řešení pro Office pomocí Instalační služba systému Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md). **Poznámka:**  Když ve vývojovém počítači vytvoříte doplněk VSTO, Visual Studio automaticky připojí **&#124;řetězec vstolocal** k této položce registru.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a> Položky registru pro oblasti formulářů aplikace Outlook
 Pokud vytvoříte vlastní oblast formuláře v doplňku VSTO pro Outlook, použijí se k registraci oblasti formuláře v Outlooku další položky registru. Tyto položky jsou vytvořeny v jiném klíči registru pro každou třídu zprávy, kterou oblast formuláře podporuje. Tyto klíče registru jsou v následujícím umístění, kde *root* je **HKEY_CURRENT_USER** nebo **HKEY_LOCAL_MACHINE**.

 *Kořenová* \\ *třída zpráv* \Software\Microsoft\Office\Outlook\FormRegions

 Podobně jako ostatní položky registru sdílené všemi doplňky VSTO vytvoří Visual Studio položky registru oblasti formuláře ve vývojovém počítači při sestavování projektu. Pokud použijete ClickOnce k nasazení doplňku VSTO, položky registru se automaticky vytvoří v počítači koncového uživatele. Pokud použijete Instalační služba systému Windows k nasazení doplňku VSTO, je nutné nakonfigurovat projekt InstallShield limit Edition tak, aby vytvořil položky registru v počítači koncového uživatele.

 Další informace o položkách registru oblasti formuláře najdete v tématu [určení umístění oblasti formuláře ve vlastním formuláři](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Další informace o oblastech formulářů Outlook najdete v tématu věnovaném [vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a> Hodnoty LoadBehavior
 Položka **LoadBehavior** v *kořenovém adresáři*\Software\Microsoft\Office \\ *název aplikace*\Addins \\ *– klíč ID doplňku* obsahuje bitovou kombinaci hodnot, které určují chování doplňku VSTO v době běhu. Nejnižší bit pořadí (hodnoty 0 a 1) označuje, jestli je doplněk VSTO aktuálně uvolněný nebo načtený. Jiné bity označují, kdy se aplikace pokusí načíst doplněk VSTO.

 Položka **LoadBehavior** má typicky nastavenou hodnotu 0, 3 nebo 16 (v desítkové soustavě), když je doplněk VSTO nainstalovaný na počítačích koncových uživatelů. Ve výchozím nastavení sada Visual Studio nastaví položku **LoadBehavior** doplňku VSTO na 3 při sestavování nebo publikování.

 V následující tabulce jsou uvedeny všechny možné hodnoty položky **LoadBehavior** . Některé popisy v této tabulce odkazují na ruční načtení doplňku VSTO nebo prostřednictvím kódu programu. Pokud chcete doplněk VSTO načíst ručně, zaškrtněte políčko vedle doplňku VSTO v dialogovém okně **Doplňky modelu COM** v aplikaci. Chcete-li načíst doplněk VSTO programově, nastavte <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> vlastnost <xref:Microsoft.Office.Core.COMAddIn> objektu, který představuje doplněk VSTO na **hodnotu true**.

|Hodnota (v desítkové soustavě)|Stav doplňku VSTO|Chování při načítání doplňku VSTO|Popis|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|uvolněné|Nečítat automaticky|Aplikace se nikdy nepokouší načíst doplněk VSTO automaticky. Uživatel se může pokusit o ruční načtení doplňku VSTO nebo doplněk VSTO se dá programově načíst.<br /><br /> Pokud je doplněk VSTO úspěšně načtený, hodnota **LoadBehavior** zůstane 0, ale stav doplňku VSTO v dialogovém okně **Doplňky modelu COM** se aktualizuje tak, aby OZNAČOVAL, že doplněk VSTO je načtený.|
|1|Načten|Nečítat automaticky|Aplikace se nikdy nepokouší načíst doplněk VSTO automaticky. Uživatel se může pokusit o ruční načtení doplňku VSTO nebo doplněk VSTO se dá programově načíst.<br /><br /> I když se v dialogovém okně **Doplňky modelu COM** označuje, že doplněk VSTO se načte po spuštění aplikace, doplněk VSTO se nenačte, dokud ho nenačtete ručně nebo programově.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** se změní na 0 a po zavření aplikace zůstane v hodnotě 0.|
|2|uvolněné|Načíst při spuštění|Aplikace se nepokouší načíst doplněk VSTO automaticky. Uživatel se může pokusit o ruční načtení doplňku VSTO nebo doplněk VSTO se dá programově načíst.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** se změní na 3 a po zavření aplikace zůstane v hodnotě 3.|
|3|Načten|Načíst při spuštění|Aplikace se pokusí načíst doplněk VSTO při spuštění aplikace. Toto je výchozí hodnota při sestavování nebo publikování doplňku VSTO v aplikaci Visual Studio.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** zůstane 3. Pokud při načítání doplňku VSTO dojde k chybě, hodnota **LoadBehavior** se změní na 2 a po zavření aplikace zůstane v 2.|
|8|uvolněné|Načíst na vyžádání|Aplikace se nepokouší načíst doplněk VSTO automaticky. Uživatel se může pokusit o ruční načtení doplňku VSTO nebo doplněk VSTO se dá programově načíst.<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** se změní na 9.|
|9|Načten|Načíst na vyžádání|Doplněk VSTO se načte jenom v případě, že ho aplikace vyžaduje, třeba když uživatel klikne na prvek uživatelského rozhraní, který používá funkce doplňku VSTO (například vlastní tlačítko na pásu karet).<br /><br /> Pokud aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** zůstane 9, ale stav doplňku VSTO v dialogovém okně **Doplňky modelu COM** se aktualizuje tak, aby OZNAČOVAL, že doplněk VSTO je momentálně načtený. Pokud při načítání doplňku VSTO dojde k chybě, hodnota **LoadBehavior** se změní na 8.|
|16|Načten|Poprvé načíst a pak načíst na vyžádání|Tuto hodnotu nastavte, pokud chcete, aby byl doplněk VSTO načtený na vyžádání. Aplikace načte doplněk VSTO, když uživatel poprvé spustí aplikaci. Když uživatel příště spustí aplikaci, načte všechny prvky uživatelského rozhraní, které jsou definované doplňkem VSTO, ale doplněk VSTO se nenačte, dokud uživatel neklikne na prvek uživatelského rozhraní, který je přidružený k doplňku VSTO.<br /><br /> Když aplikace úspěšně načte doplněk VSTO, hodnota **LoadBehavior** v průběhu načítání doplňku VSTO zůstane 16. Po zavření aplikace se hodnota **LoadBehavior** změní na 9.|

## <a name="see-also"></a>Viz také
- [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
 