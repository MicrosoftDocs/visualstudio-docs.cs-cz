---
title: Nasazení řešení Office pomocí Instalační služba systému Windows
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1336af7469b030492b486004940b730d372760bb
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90807960"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Nasazení řešení Office pomocí Instalační služba systému Windows

Naučte se vytvářet Instalační služba systému Windows pro vaše řešení pro Office pomocí [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

Pomocí sady Visual Studio k vytvoření Instalační služba systému Windows můžete nasadit řešení pro Office, které vyžaduje přístup správce v počítači koncového uživatele. Například můžete použít takový soubor k instalaci řešení pouze jednou pro všechny uživatele počítače. Řešení Office můžete nasadit také pomocí technologie ClickOnce, ale toto řešení je nutné nainstalovat samostatně pro každého uživatele počítače.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-topic"></a>V tomto tématu

- [Stáhnout ukázky doplňku VSTO](#Download)

- [Získat InstallShield s omezením edice](#Obtain)

- [Rozhodnutí o tom, jak udělit důvěru k řešení](#ApplySecurity)

- [Vytvořit projekt instalace](#Create)

- [Přidat výstup projektu](#Add)

- [Přidat manifesty nasazení a aplikace](#AddD)

- [Konfigurace závislých komponent jako požadovaných součástí](#Configure)

- [Určete, kam chcete řešení nasadit v počítači uživatele.](#Location)

- [Konfigurace doplňku VSTO](#ConfigureRegistry)

- [Konfigurace přizpůsobení na úrovni dokumentu](#ConfigureDocument)

- [Sestavení projektu instalace](#Build)

Další informace o tom, jak nasadit řešení pro Office pomocí ClickOnce, najdete v tématu [nasazení řešení pro Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

Informace o tom, jak vytvořit soubor Instalační služba systému Windows pomocí [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , najdete v tématu [nasazení nástrojů sady Visual Studio 2010 pro řešení Office pomocí Instalační služba systému Windows](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10)).

## <a name="download-samples"></a><a name="Download"></a>Stažení ukázek
Toto téma se týká následujících ukázek ke stažení.

|Ukázka<br /><br />|Popis<br /><br />|
|----------|---------------|
|[ExcelAddIn](https://code.msdn.microsoft.com/VSTO-Deploy-an-Office-fbcc09ad)<br /><br />|Doplněk VSTO pro Excel, který můžete nainstalovat na počítač, na kterém běží 32 nebo 64 verze systému Office.<br /><br />|
|[ExcelWorkbook](https://code.msdn.microsoft.com/VSTO-Deploy-a-Customization-f70fae33)<br /><br />|Přizpůsobení na úrovni dokumentu aplikace Excel, které můžete nainstalovat na počítač, na kterém běží 32 nebo 64 bitová verze systému Office.<br /><br />|

## <a name="decide-how-to-grant-trust-to-the-solution"></a><a name="ApplySecurity"></a>Rozhodnutí o tom, jak udělit důvěru k řešení
Předtím, než může být řešení spuštěno v počítačích uživatelů, je nutné udělit důvěryhodnost jedním z následujících způsobů nebo uživatelé musí při instalaci řešení reagovat na výzvu k zadání vztahu důvěryhodnosti.

- Podepište manifesty pomocí certifikátu, který identifikuje známého a důvěryhodného vydavatele. Další informace najdete v tématu [důvěřování řešení pomocí podepisování manifestů aplikace a nasazení](../vsto/granting-trust-to-office-solutions.md#Signing).

- Nainstalujte řešení do adresáře Program Files v počítači uživatele.

> [!NOTE]
> V případě přizpůsobení na úrovni dokumentu musí být umístění dokumentu také důvěryhodné. Další informace najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

## <a name="get-installshield-limited-edition"></a><a name="Obtain"></a>Získat InstallShield s omezením edice

Soubor Instalační služba systému Windows můžete vytvořit pomocí nástroje InstallShield omezené Edition (ISLE), který je zdarma, pokud jste nainstalovali aplikaci Visual Studio. ISLE nahrazuje funkce šablon projektů pro nastavení a nasazení, které jsou k dispozici v předchozích verzích sady Visual Studio.

### <a name="to-get-installshield-limited-edition"></a>Získání InstallShield omezené edice

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

   Otevře se dialogové okno **Nový projekt** .

2. V podokně šablony rozbalte položku **jiné typy projektů**a pak zvolte šablonu **instalace a nasazení** .

3. V seznamu typů projektů pro **instalaci a nasazení**zvolte možnost **Povolit InstallShield s omezením edice**a pak klikněte na tlačítko **OK** .

   Zobrazí se stránka, která poskytuje informace o tom, jak získat InstallShield s omezením edice.

4. Na této stránce vyberte odkaz **Přejít na web stáhnout** .

5. Na stránce pro stažení pro program InstallShield Limited Edition zadejte požadované informace do příslušných polí a pak zvolte odkaz **Stáhnout nyní** .

   Po stažení, instalaci a aktivaci produktu se v aplikaci Visual Studio zobrazí šablona **projektu InstallShield s omezeným vydáním** .

## <a name="create-a-setup-project"></a><a name="Create"></a>Vytvořit projekt instalace

1. V nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevřete projekt Office, který chcete nasadit.

   Ukázky doplňku VSTO spojené s tímto tématem obsahují projekt s názvem **ExcelAddIn**. Ukázky přizpůsobení na úrovni dokumentu obsahují projekt s názvem **ExcelWorkbook**. Toto téma bude odkazovat na projekt sady Office ve vašem řešení pomocí jednoho z těchto dvou názvů.

2. Na řádku nabídek klikněte na položku **soubor**  >  **Přidat**  >  **Nový projekt**.

   Otevře se dialogové okno **Přidat nový projekt** .

3. V podokně šablony rozbalte položku **jiné typy projektů**a pak zvolte šablonu **instalace a nasazení** .

4. V seznamu typů projektů pro **nastavení a nasazení**zvolte možnost **Projekt InstallShield-omezená edice**, pojmenujte projekt a klikněte na tlačítko **OK** .

   Projekt instalace InstallShield, který jste vytvořili, se zobrazí ve vašem řešení.

   Ukázky pro toto téma obsahují projekt instalace s názvem **OfficeAddInSetup**. Toto téma bude odkazovat na projekt instalace ve vašem řešení pomocí stejného názvu.

## <a name="add-the-project-output"></a><a name="Add"></a>Přidat výstup projektu

Projekt **OfficeAddInSetup** nakonfigurujete tak, aby zahrnoval výstup projektu Office. V případě projektů doplňku VSTO je výstupem projektu pouze sestavení řešení. Pro projekty přizpůsobení na úrovni dokumentu zahrnuje výstup projektu nejen sestavení řešení, ale také samotný dokument.

### <a name="to-add-the-project-output"></a>Chcete-li přidat výstup projektu

1. V **Průzkumník řešení**rozbalte uzel projektu **OfficeAddInSetup** a pak zvolte soubor **pomocníka projektu** , který je znázorněn na následujícím obrázku.

   ![Soubor pomocníka projektu v Průzkumník řešení](../vsto/media/installshield-projectassistant.png "Soubor pomocníka projektu v Průzkumník řešení")

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

3. V dolní části stránky **Pomocník projektu** klikněte na tlačítko **soubory aplikace** , které ukazuje následující obrázek.

   ![Tlačítko soubory aplikace](../vsto/media/installshield-applicationfiles.png "Tlačítko soubory aplikace")

4. Na stránce **soubory aplikace** klikněte na tlačítko **Přidat výstupy projektu** .

5. V dialogovém okně **selektor výstupu sady Visual Studio** zaškrtněte políčko **primární výstup** a pak klikněte na tlačítko **OK** .

## <a name="add-the-deployment-and-application-manifests"></a><a name="AddD"></a>Přidat manifesty nasazení a aplikace

1. Na stránce **soubory aplikace** klikněte na tlačítko **Přidat soubory** .

2. V dialogovém okně **otevřít** přejděte do výstupního adresáře projektu **ExcelAddIn** .

   Výstupní adresář je obvykle podsložkou **bin\Release** kořenového adresáře projektu v závislosti na konfiguraci sestavení, kterou zvolíte.

3. Ve výstupním adresáři zvolte soubory **ExcelAddIn. VSTO** a **ExcelAddIn.dll. manifest** a pak klikněte na tlačítko **otevřít** .

   Stránka **soubory aplikace** nyní obsahuje výstupní soubor projektu, manifest nasazení a manifest aplikace, jak ukazuje následující obrázek.

   ![Výstupní soubory projektu instalace.](../vsto/media/installshield-outputfiles.png "Výstupní soubory projektu instalace.")

## <a name="configure-the-dependent-components-as-prerequisites"></a><a name="Configure"></a>Konfigurace závislých komponent jako požadovaných součástí

V aplikaci pro instalaci musíte zahrnout nejen následující součásti, ale také všechny další komponenty, které jsou potřebné pro spuštění vašeho řešení.

- Verze .NET Framework, na kterou se vaše řešení pro Office zaměřuje

- Rozhraní Microsoft Visual Studio 2010 Tools for Office runtime.

### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Přidejte .NET Framework 4 nebo .NET Framework 4,5 jako požadavek.

1. V **Průzkumník řešení**rozbalte uzel projektu **OfficeAddInSetup** , rozbalte uzel **zadat data aplikace** a pak zvolte soubor **redistribuovatelného** souboru, který je znázorněn na následujícím obrázku.

   ![Distribuovatelný soubor v Průzkumník řešení](../vsto/media/installshield-redistributablesfile.png "Distribuovatelný soubor v Průzkumník řešení")

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

   Otevře se stránka **distribuovatelné** součásti.

3. V seznamu distribuovatelné součásti zaškrtněte políčko pro verzi .NET Framework, na kterou je vaše řešení cíleno.

   Například pokud vaše řešení cílí na [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , zaškrtněte políčko **Microsoft .NET Framework 4,5 úplné** . Může se zobrazit dialogové okno s dotazem, zda chcete nainstalovat distribuovatelné komponenty, které InstallShield vyžaduje předtím, než budete moci součást přidat jako požadavek. Pokud se toto dialogové okno nezobrazí, komponenta již v počítači existuje.

4. Pokud se zobrazí toto dialogové okno, klikněte na tlačítko **ne** .

### <a name="add-the-visual-studio-2010-tools-for-office-runtime"></a><a name="AddToolsForOffice"></a>Přidejte sadu Visual Studio 2010 Tools for Office runtime.

Stránka **distribuovatelné** obsahuje položku s názvem **Microsoft VSTO 2010 Runtime**, ale odkazuje na starší verzi modulu runtime. Proto můžete ručně vytvořit konfigurační soubor, který odkazuje na nejnovější verzi. Pak je nutné umístit tento soubor do stejného adresáře jako konfigurační soubory pro všechny ostatní položky, které se zobrazí na stránce **distribuovatelné** .

#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Přidání nástrojů sady Visual Studio 2010 pro Office runtime jako předpokladu

1. Otevřete Poznámkový blok a vložte následující kód XML do textového souboru.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <SetupPrereq>
   <conditions>
       <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>
   <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>
   </conditions>
   <files>
       <file LocalFile="<ISProductFolder>\SetupPrerequisites\VSTOR\vstor_redist.exe" URL="http://download.microsoft.com/download/C/0/0/C001737F-822B-48C2-8F6A-CDE13B4B9E9C/vstor_redist.exe" CheckSum="88b8aa9e8c90818f98c80ac4dd998b88" FileSize=" 0,40117912"></file>
   </files>
   <execute file="vstor_redist.exe" returncodetoreboot="1641,3010" requiresmsiengine="1">
   </execute>
   <properties Id="{15965040-56BB-49B8-A88F-3525C48D9BA8}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>

   </SetupPrereq>
   ```

2. Vygenerujte identifikátor GUID v aplikaci Visual Studio. V nabídce **nástroje** vyberte možnost **vytvořit GUID**.

3. V programu **generátor identifikátorů GUID** zvolte tlačítko možnosti **Formát registru** , klikněte na tlačítko **Kopírovat** a pak klikněte na tlačítko **ukončit** .

4. V programu Poznámkový blok nahraďte text, na který se **odkazuje identifikátor GUID** , VLOŽENÍm identifikátoru GUID na místo.

   Element ** &lt; Properties &gt; ** souboru se podobá následujícímu.

   ```xml
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>
   ```

5. Na panelu nabídek v programu Poznámkový **File**blok klikněte na  >  **Uložit**soubor.

6. V dialogovém okně **Uložit jako** vyhledejte složku **plocha** .

7. V seznamu **Uložit jako typ** vyberte možnost **všechny soubory (&#42;. &#42;)**.

8. Do pole **název souboru** zadejte **Visual Studio 2010 Tools for Office runtime. prq**a pak klikněte na tlačítko **Uložit** .

   > [!NOTE]
   > Ujistěte se, že na konec názvu souboru přidáte **. prq** , abyste tento soubor identifikovali jako požadovaný soubor.

9. Zavřete Poznámkový blok.

10. Ze složky **plocha** zkopírujte soubor *Visual Studio 2010 Tools for Office runtime. prq* do jednoho z následujících adresářů v počítači.

   Pro 32 operační systémy: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites \\ *

   Pro 64 operační systémy: *% ProgramFiles (x86)% \ 2013LE \ SetupPrerequisites \\ *

11. V rámci **Redistribuovatelné** stránky projektu InstallShield klikněte na tlačítko **aktualizovat** , čímž aktualizujete seznam distribuovatelných komponent, jak je znázorněno na následujícím obrázku.

   ![Tlačítko Aktualizovat](../vsto/media/installshield-refreshbutton.png "Tlačítko Aktualizovat")

12. V seznamu redistribuovatelných komponent zaškrtněte políčko **Visual Studio 2010 Tools for Office runtime** .

   Může se zobrazit dialogové okno s dotazem, zda chcete nainstalovat Distribuovatelný součást. Pokud se toto dialogové okno nezobrazí, můžete přeskočit na adresu [určení, kde chcete řešení nasadit, v části počítač uživatele](#Location) v tomto tématu.

13. Pokud se zobrazí toto dialogové okno, klikněte na tlačítko **ne** .

## <a name="specify-where-to-install-the-solution-on-the-users-computer"></a><a name="Location"></a>Určete, kam se má v počítači uživatele nainstalovat řešení.

1. V **Průzkumník řešení**rozbalte uzel **OfficeAddInSetup** , rozbalte uzel **Uspořádat nastavení** a pak zvolte soubor **Obecné informace** .

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

3. V seznamu vlastností klikněte na tlačítko **Procházet** vedle vlastnosti **INSTALLDIR** .

4. V dialogovém okně **nastavit INSTALLDIR** vyberte složku v počítači uživatele, do které chcete řešení nainstalovat.

   > [!NOTE]
   > V dialogovém okně **nastavit INSTALLDIR** můžete také vytvořit podadresáře tak, že otevřete místní nabídku pro všechny složky v seznamu.

## <a name="configure-a-vsto-add-in"></a><a name="ConfigureRegistry"></a>Konfigurace doplňku VSTO

Můžete určit, jestli se má doplněk VSTO nainstalovat pro všechny uživatele počítače (pro jednotlivé počítače), nebo jenom pro uživatele, který provádí instalaci (podle uživatele).

Pokud chcete podporovat instalace pro jednotlivé počítače, vytvořte dva samostatné instalační programy. Instalační programy můžete rozdělit na základě verze Office (32 bitů a 64 bitů) nebo verze Windows (32-bit a 64), kterou uživatel používá.

Instalace pro jednotlivé uživatele vyžadují jenom jeden instalační program bez ohledu na verzi Office nebo Windows.

> [!NOTE]
> Tato část platí jenom v případě, že nasazujete doplněk VSTO. Pokud nasazujete přizpůsobení na úrovni dokumentu, můžete okamžitě přejít do části [Konfigurace přizpůsobení na úrovni dokumentu](#ConfigureDocument) .

### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Určení, zda chcete podporovat instalace vázané na uživatele nebo na počítač

1. V **Průzkumník řešení**rozbalte uzel projektu **OfficeAddInSetup** , rozbalte uzel **Uspořádat nastavení** a pak zvolte soubor **Obecné informace** .

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

   Zobrazí se vlastnosti projektu instalace.

3. V seznamu vlastnosti **AllUSERS** určete, zda chcete toto řešení nainstalovat pro všechny uživatele počítače, nebo pouze pro uživatele, který toto řešení instaluje.

   Chcete-li nainstalovat doplněk VSTO pro aktuálního uživatele, vyberte možnost **allusers = "" (instalace vázaná na uživatele)**. Chcete-li nainstalovat doplněk VSTO pro všechny uživatele počítače, vyberte možnost **AllUsers = 1 (instalace vázaná na počítač)** .

   V dalším postupu vytvoříte klíče registru, které aplikaci Office umožní zjistit a načíst doplněk VSTO. Viz [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-create-registry-keys"></a>Vytvoření klíčů registru

1. V **Průzkumník řešení**vyberte uzel **pomocníka projektu** .

   Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

2. V dolní části stránky **Pomocník projektu** klikněte na tlačítko **registr aplikace** , které ukazuje následující obrázek.

   ![Tlačítko registru aplikace](../vsto/media/installshield-applicationregistry.gif "Tlačítko registru aplikace")

   Zobrazí se stránka **registr aplikace** .

3. V části chcete **nakonfigurovat data registru, která bude aplikace instalovat?** klikněte na tlačítko **Ano** .

4. V seznamu **zobrazení registru cílového počítače** přidejte klíčovou hierarchii, která umožňuje typ instalačního programu, který chcete vytvořit.

   Cesta, kterou v této části nakonfigurujete, závisí na tom, jestli vytváříte instalační program pro jednotlivé uživatele nebo instalační program pro jednotlivé počítače.

   **Instalační program pro jednotlivé uživatele**

   **HKEY_CURRENT_USER \Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**

   **Instalační programy pro jednotlivé počítače založené na verzi Office**

| Verze sady Office<br /><br /> | Konfigurační cesta InstallShield<br /><br /> |
|----------------------------| - |
| 32bitová<br /><br /> | **HKEY_LOCAL_MACHINE \SOFTWARE (32 bitů) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64bitová<br /><br /> | **HKEY_LOCAL_MACHINE \SOFTWARE (64 bitů) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Instalační programy pro jednotlivé počítače založené na verzi Windows**

| Verze systému Windows<br /><br /> | Konfigurační cesta InstallShield<br /><br /> |
|-----------------------------| - |
| 32bitová<br /><br /> | **HKEY_LOCAL_MACHINE \SOFTWARE (32 bitů) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64bitová<br /><br /> | **HKEY_LOCAL_MACHINE \SOFTWARE (32 bitů) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE \SOFTWARE (64 bitů) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]
   > Instalační služba systému Windows pro 64 vyžaduje dvě cesty registru, protože je možné, že uživatelé spouštějí 32 a 64 bitových verzí systému Office v počítači, na kterém 64 běží systém Windows v 16bitovém.

   > [!NOTE]
   > Jako osvědčený postup spusťte název doplňku VSTO s názvem vaší společnosti. Tato konvence zvyšuje pravděpodobnost, že klíč bude jedinečný a snižuje pravděpodobnost konfliktu s doplňkem VSTO od jiného dodavatele. Doplňky, které mají stejný název, mohou například přepsat každý druhý registrační klíč. Tento přístup nemůže zaručit, že klíč bude jedinečný, ale může omezit potenciální kolizí názvů.

5. Po vytvoření hierarchie klíčů otevřete místní nabídku pro klíč **klíče SampleCompany. ExcelAddIn** , zvolte možnost **Nový**a pak zvolte možnost **hodnota řetězce**.

   V seznamu **data registru cílového počítače** se zobrazí nová řetězcová hodnota. Název řetězcové hodnoty je zvýrazněný, takže ho můžete přejmenovat.

6. Přejmenujte hodnotu **Description**.

7. Tento postup opakujte, pokud chcete vytvořit následující hodnoty.

|Typ hodnoty<br /><br />|Název<br /><br />|
|--------------|--------|
|Řetězcová hodnota<br /><br />|**FriendlyName**<br /><br />|
|Hodnota DWORD<br /><br />|**LoadBehavior**<br /><br />|
|Řetězcová hodnota<br /><br />|**Zřetel**<br /><br />|

8. Otevřete místní nabídku hodnoty **Popis** a pak zvolte možnost **Upravit**.

   Zobrazí se dialogové okno **Upravit data** .

9. Do textového pole **data hodnoty** zadejte **Excel demo Add-in**a pak klikněte na tlačítko **OK** .

   Tento popis se zobrazí, když uživatel otevře aplikaci Office, otevře dialogové okno **Možnosti** a potom v podokně **Doplňky** zvolte doplněk VSTO.

10. Otevřete místní nabídku hodnoty **FriendlyName** a zvolte možnost **Upravit**.

   Zobrazí se dialogové okno **Upravit data** .

11. Do textového pole **data hodnoty** zadejte **Excel demo Add-in**a pak klikněte na tlačítko **OK** .

   Tento řetězec se zobrazí v dialogovém okně **Doplňky modelu COM** v aplikaci Office. Ve výchozím nastavení je hodnota řetězce ID doplňku VSTO.

12. Otevřete místní nabídku pro hodnotu **LoadBehavior** a pak zvolte možnost **Upravit**.

   Zobrazí se dialogové okno **Upravit data** .

13. Do textového pole **data hodnoty** zadejte **3**a pak klikněte na tlačítko **OK** .

   Hodnota 3 načte doplněk VSTO při spuštění aplikace. Další informace o hodnotách LoadBehavior najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

14. Otevřete místní nabídku pro hodnotu **manifestu** a pak zvolte možnost **Upravit**.

   Zobrazí se dialogové okno **Upravit data** .

15. Do textového pole **data hodnoty** zadejte **soubor:///[INSTALLDIR] ExcelAddIn. VSTO | vstolocal**a pak klikněte na tlačítko **OK** .

   Sada Visual Studio 2010 Tools for Office runtime používá tuto cestu k vyhledání manifestu nasazení. Část **[INSTALLDIR]** této cesty je makro, které se mapuje na vlastnost **INSTALLDIR** na stránce vlastností **Obecné informace** v projektu instalace InstallShield. Tato vlastnost určuje umístění v cílovém počítači pro instalaci doplňku VSTO. Přípona **| vstolocal** zajišťuje, že vaše řešení je načteno z instalační složky, nikoli z mezipaměti ClickOnce.

> [!IMPORTANT]
> Pokud vytvoříte vlastní oblast formuláře v doplňku VSTO pro Outlook, musíte vytvořit další položky registru pro registraci oblasti v Outlooku. Další informace najdete v tématu [položky registru pro oblasti formulářů Outlooku](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).

## <a name="configure-a-document-level-customization"></a><a name="ConfigureDocument"></a>Konfigurace přizpůsobení na úrovni dokumentu

Tato část platí pouze v případě, že nasazujete přizpůsobení na úrovni dokumentu. Pokud doplněk VSTO nasazujete, můžete hned přejít k části [sestavení projektu instalace](#Build) .

Přizpůsobení na úrovni dokumentu nepoužívají klíče registru. Místo toho vlastní vlastnosti dokumentu obsahují umístění manifestu nasazení.

Chcete-li upravit vlastní vlastnosti, vytvořte program, který odebere přizpůsobení na úrovni dokumentu z dokumentu, upraví příslušné vlastnosti a pak znovu připojí přizpůsobení k dokumentu. Pak vytvoříte vlastní akci, která spustí program, a přidáte tuto akci do projektu instalace.

### <a name="to-create-a-program-that-modifies-document-properties"></a>Vytvoření programu, který upraví vlastnosti dokumentu

1. Na řádku nabídek klikněte na položku **soubor**  >  **Přidat**  >  **Nový projekt**.

   Zobrazí se dialogové okno **Přidat nový projekt** .

2. V podokně šablony pod uzlem pro jazyk, který chcete použít, vyberte složku **Windows** .

3. V seznamu typů projektů pro **systém Windows**vyberte šablonu **Konzolová aplikace** .

4. Pojmenujte projekt **SetExcelDocumentProperties**a pak klikněte na tlačítko **OK** .

5. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** , otevřete místní nabídku uzlu projektu **SetExcelDocumentProperties** a poté zvolte možnost **Přidat odkaz**.

6. V dialogovém okně **Správce odkazů** zvolte kartu **rozšíření** a potom zaškrtněte políčko vedle následujících sestavení a poté klikněte na tlačítko **OK** .

   - Microsoft. VisualStudio. Tools. Applications. Runtime

   - Microsoft. VisualStudio. Tools. Applications. ServerDocument

7. V **Průzkumník řešení**vyberte soubor **program.cs** (pro aplikace v jazyce C#) nebo soubor **Module1. vb** (pro Visual Basic aplikace).

8. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

9. Obsah celého souboru nahraďte následujícím kódem.

[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]

10. Zkompilujte projekt.

### <a name="to-add-a-custom-action-that-runs-your-program"></a>Přidání vlastní akce, která spustí program

1. V **Průzkumník řešení**rozbalte uzel projektu **OfficeAddInSetup** a pak zvolte soubor **pomocníka projektu** , který je znázorněn na následujícím obrázku.

   ![Soubor pomocníka projektu v Průzkumník řešení](../vsto/media/installshield-projectassistant.png "Soubor pomocníka projektu v Průzkumník řešení")

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

3. V dolní části stránky **Pomocník projektu** klikněte na tlačítko **soubory aplikace** , které ukazuje následující obrázek.

   ![Tlačítko soubory aplikace](../vsto/media/installshield-applicationfiles.png "Tlačítko soubory aplikace")

4. Na stránce **soubory aplikace** klikněte na tlačítko **Přidat výstupy projektu** .

   Zobrazí se dialogové okno **selektor výstupu sady Visual Studio** .

5. V uzlu **SetExcelDocumentProperties** zaškrtněte políčko **primární výstup** a pak klikněte na tlačítko **OK** .

6. V **Průzkumník řešení**pod uzlem **OfficeAddInSetup** rozbalte uzel **definovat požadavky na nastavení a akce** a pak zvolte složku **vlastní akce** .

7. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

   Seznam událostí se zobrazí v podokně vedle obrazovky.

   > [!NOTE]
   > V programu InstallShield omezená edice jsou k dispozici pouze některé události, které jsou uvedeny v tomto seznamu. V tomto postupu spustíte program pomocí události **dialog po instalaci dokončit úspěch** .

8. V seznamu událostí v části **vlastní akce během instalace**otevřete místní nabídku pro událost **dialogového okna po instalaci dokončit úspěch** a pak zvolte možnost **nový soubor exe**.

   Vlastní akce s názvem **NewCustomAction1** se zobrazí v rámci události **dialog po dokončení instalace dokončit úspěch** . Sada vlastností vlastní akce se zobrazí v podokně vedle událostí.

   > [!IMPORTANT]
   > V seznamu událostí se zobrazí dvě události **dialogu dokončit úspěšné dokončení instalačního programu** . Ujistěte se, že jste zvolili instanci **dialogového okna po dokončení instalace dokončit úspěch** , která se zobrazí v části **vlastní akce během instalace** uzlu.

9. V seznamu vlastnosti **umístění zdroje** vyberte možnost **nainstalováno s produktem**.

10. Klikněte na tlačítko **Procházet** vedle vlastnosti **název souboru** .

11. V dialogovém okně **vyhledat cílový soubor** přejděte do souboru **SetExcelDocumentProperties. Primary. Output** a pak klikněte na tlačítko **otevřít** .

    Umístění tohoto souboru závisí na složce, kterou jste zadali pro vlastnost **INSTALLDIR** projektu instalace. Například pokud nastavíte tuto vlastnost na složku s názvem **[osobnísložka] DemoWorkbookApp**, můžete najít soubor **SetExcelDocumentProperties. Primary. Output** procházením na **[složkaprogramfiles] \DemoWorkbookApp**.

    V několika dalších krocích získáte ID řešení dokumentu a pak toto ID předáte jako parametr do konzolové aplikace. Také předáte umístění dokumentu, manifestu nasazení a sestavení dokumentu.

12. Otevřete místní nabídku projektu **ExcelWorkbook** a v závislosti na operačním systému zvolte možnost **Otevřít složku v Průzkumníku Windows** nebo **Otevřít složku v Průzkumníku souborů** .

    Otevře se složka, která obsahuje vaše řešení.

13. V programu Poznámkový blok otevřete soubor projektu svého řešení. U Visual Basic projektů je název souboru *ExcelWorkbook. vbproj*. V případě projektů v jazyce C# je název souboru *ExcelWorkbook. csproj*.

14. V souboru projektu vyhledejte element ** &lt; SolutionId &gt; ** , zkopírujte jeho hodnotu do schránky a pak zavřete Poznámkový blok.

    Tuto hodnotu předáte do aplikace konzoly jako parametr.

15. Na stránce vlastnosti **NewCustomAction1**nastavte vlastnost **příkazového řádku** na následující řádek textu.

   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"
   ```

16. Nahraďte **ID řešení** číslem ID řešení, které jste zkopírovali do schránky.

   > [!IMPORTANT]
   > Otestujte instalační program, abyste ověřili, že aplikace konzoly, kterou tato vlastní akce spustí, má přístup k dokumentům v adresáři [INSTALLDIR]. Některé adresáře v počítači uživatele mohou vyžadovat přístup správce (například adresář Program Files). Pokud nasazujete řešení do adresáře, který vyžaduje přístup správce, měli byste otevřít dialogové okno **vlastnosti** souboru *setup.exe* , vybrat kartu **Kompatibilita** a potom před distribucí instalačního programu zaškrtnout políčko **Spustit tento program jako správce** . Pokud nechcete, aby uživatelé spustili instalační program s oprávněními správce, nastavte vlastnost [INSTALLDIR] na adresář, ke kterému má uživatel pravděpodobně již přístup, například adresář **dokumentů** . Další informace najdete v části [určení, kam chcete řešení nainstalovat, v části počítač uživatele](#Location) v tomto tématu.

## <a name="build-the-setup-project"></a><a name="Build"></a>Sestavení projektu instalace

1. V **Průzkumník řešení**rozbalte uzel **Příprava pro vydání** a pak zvolte soubor **vydání** .

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **otevřené**.

   Průzkumník **sestavení** se otevře v bočním podokně, abyste mohli vybrat typ vydaných verzí, který chcete vytvořit.

3. V Průzkumníku **sestavení** vyberte složku **možnost SingleImage** .

4. V podokně vedle Průzkumníka **sestavení** klikněte na kartu **Setup.exe** .

5. Na stránce vlastností **Setup.exe** v seznamu **umístění požadavků InstallShield** vyberte možnost **stáhnout z webu**.

6. Na panelu nabídek vyberte možnost **sestavit**  >  **Configuration Manager**.

7. V seznamu **aktivní konfigurace řešení** vyberte možnost **možnost SingleImage**.

8. V tabulce **kontexty projektu** ve sloupci **Konfigurace** projektu **OfficeAddInSetup** zvolte možnost **možnost SingleImage**a poté klikněte na tlačítko **Zavřít** .

9. Na panelu nabídek vyberte sestavení sestavení **Build**  >  **OfficeAddInSetup**.

   Po dokončení sestavení můžete najít soubor *setup.exe* projektu **OfficeAddInSetup** v následujícím umístění: <em>OfficeAddInSetupProjectRoot</em>**\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1 \\ **

## <a name="see-also"></a>Viz také

- [Požadavky na řešení systému Office pro nasazení](/previous-versions/bb608617(v=vs.110))
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md)
- [Přehled vlastních vlastností dokumentu](../vsto/custom-document-properties-overview.md)
- [Udělení vztahu důvěryhodnosti řešením pro systém Office](../vsto/granting-trust-to-office-solutions.md)
- [Udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md)
- [Nasazení nástrojů sady Visual Studio 2010 pro řešení Office pomocí Instalační služba systému Windows](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))