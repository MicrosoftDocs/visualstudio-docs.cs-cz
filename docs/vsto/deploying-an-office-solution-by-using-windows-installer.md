---
title: Nasazení řešení Office s použitím Instalační služby systému Windows
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3e811fac767e8b89f0a6958511c54642f07190cf
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673052"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Nasazení řešení Office s použitím Instalační služby systému Windows
Zjistěte, jak vytvořit instalační program Windows pro řešení Office s použitím [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  

Pomocí sady Visual Studio k vytvoření Windows Installer můžete nasadit řešení pro Office, která vyžaduje oprávnění správce v počítači koncového uživatele. Například můžete použít takový soubor k instalaci řešení pouze jednou pro všechny uživatele počítače. Můžete také nasadit řešení pro Office s použitím technologie ClickOnce, ale tato řešení musí být nainstalováno odděleně pro každého uživatele počítače.  


## <a name="in-this-topic"></a>V tomto tématu  

- [Stáhněte si ukázky doplňku VSTO](#Download)  

- [Získejte InstallShield Limited Edition](#Obtain)  

- [Rozhodování o způsobu zajištění důvěryhodnosti řešení](#ApplySecurity)  

- [Vytvoření projektu instalace](#Create)  

- [Přidání výstupu projektu](#Add)  

- [Přidejte manifesty nasazení a aplikace](#AddD)  

- [Konfigurace závislých součástí jako předpokladů](#Configure)  

- [Zadejte, kam chcete nasadit řešení na počítači uživatele](#Location)  

- [Konfigurace doplňku VSTO](#ConfigureRegistry)  

- [Konfigurace přizpůsobení na úrovni dokumentu](#ConfigureDocument)  

- [Sestavit projekt instalace](#Build)  

Další informace o tom, jak nasadit řešení pro Office s použitím technologie ClickOnce naleznete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  

Informace o tom, jak vytvořit soubor Instalační služby systému Windows s použitím [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], naleznete v tématu [nasazení Visual Studio 2010 Tools pro Office řešení pomocí Instalační služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=201807).  


## <a name="Download"></a>Stáhnout ukázky  
Toto téma odkazuje na následující ukázky ke stažení.  



|Ukázka<br /><br />|Popis<br /><br />|  
|----------|---------------|  
|[ExcelAddIn](http://go.microsoft.com/fwlink/?LinkID=275492)<br /><br />|VSTO Excelový doplněk, který můžete nainstalovat na počítač, na kterém běží v 32bitové nebo 64bitové verzi systému Office.<br /><br />|  
|[ExcelWorkbook](http://go.microsoft.com/fwlink/?LinkID=275493)<br /><br />|Přizpůsobení úrovni dokumentu aplikace Excel, který můžete nainstalovat na počítač, na kterém běží v 32bitové nebo 64bitové verzi systému Office.<br /><br />|  

## <a name="ApplySecurity"></a>Rozhodování o způsobu zajištění důvěryhodnosti řešení  
Předtím, než můžete řešení spustit v počítačích uživatelů, je nutné udělit důvěryhodnost jedním z následujících způsobů nebo uživatelé musí zareagovat na výzvu vztahu důvěryhodnosti při instalaci řešení.  


- Podepište manifesty pomocí certifikátu, který identifikuje známé a důvěryhodné vydavatele. Další informace najdete v tématu [důvěryhodnosti řešení pomocí podepsání manifestů aplikace a nasazení](../vsto/granting-trust-to-office-solutions.md#Signing).  

- Nainstalujte řešení do adresáře Program Files na počítači uživatele.  

> [!NOTE]  
> Přizpůsobení na úrovni dokumentu umístění dokumentu musí také být důvěryhodný. Další informace najdete v tématu [udělit důvěryhodnost dokumenty](../vsto/granting-trust-to-documents.md).  


## <a name="Obtain"></a>Získejte InstallShield Limited Edition  
Vytvořit soubor Instalační služby systému Windows pomocí programu InstallShield Limited Edition (ISLE), které je zdarma, pokud jste nainstalovali aplikaci Visual Studio. Program ISLE nahrazuje funkce šablon projektů instalace a nasazení, které nabízí předchozí verze sady Visual Studio.  


### <a name="to-get-installshield-limited-edition"></a>Chcete-li získat program InstallShield Limited Edition  

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  

   **Nový projekt** zobrazí se dialogové okno.  

2. V podokně šablony rozbalte **ostatní typy projektů**a klikněte na tlačítko **instalace a nasazení** šablony.  

3. V seznamu typů projektů **instalace a nasazení**, zvolte **Povolit InstallShield Limited Edition**a klikněte na tlačítko **OK** tlačítko.  

   Zobrazí se stránka s informacemi o tom, jak získat program InstallShield Limited Edition.  

4. Na této stránce zvolte **přejít na web stažení** odkaz.  

5. Na stránce pro stahování pro InstallShield Limited Edition, zadejte požadované informace do příslušných polí a klikněte na tlačítko **Stáhnout** odkaz.  

   Po stažení, instalaci a aktivaci produktu **projektu InstallShield Limited Edition** šablony se zobrazí v sadě Visual Studio.  


## <a name="Create"></a>Vytvoření projektu instalace  

1. V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otevřete projekt sady Office, kterou chcete nasadit.  

   Doplněk VSTO ukázky, které jsou spojeny s tímto tématem obsahují projekt s názvem **ExcelAddIn**. Ukázky přizpůsobení na úrovni dokumentu obsahují projekt s názvem **ExcelWorkbook**. Toto téma bude odkazovat na projekt systému Office ve vašem řešení pomocí jednoho z těchto dvou názvů.  

2. V panelu nabídky zvolte **souboru** > **přidat** > **nový projekt**.  

   **Přidat nový projekt** zobrazí se dialogové okno.  

3. V podokně šablony rozbalte **ostatní typy projektů**a klikněte na tlačítko **instalace a nasazení** šablony.  

4. V seznamu typů projektů **instalace a nasazení**, zvolte **projektu InstallShield Limited Edition**, pojmenujte projekt a klikněte na tlačítko **OK** tlačítko.  

   Který jste vytvořili projekt instalace InstallShield se zobrazí ve vašem řešení.  

   Vzorky pro toto téma obsahují instalační projekt s názvem **OfficeAddInSetup**. Toto téma bude odkazovat na nastavení projektu ve vašem řešení pomocí stejného názvu.  


## <a name="Add"></a>Přidání výstupu projektu  
Můžete nakonfigurovat **OfficeAddInSetup** projektu pro zahrnutí výstupu projektu Office. Pro projekty doplňků VSTO výstup projektu je pouze sestavení řešení. Výstup projektu pro projektů přizpůsobení na úrovni dokumentu zahrnuje nejen sestavení řešení, ale také samotný dokument.  


### <a name="to-add-the-project-output"></a>Chcete-li přidat výstup projektu  

1. V **Průzkumníka řešení**, rozbalte **OfficeAddInSetup** uzel projektu a klikněte na tlačítko **Project Assistant** soubor, který ukazuje následující obrázek.  

   ![Průvodce nastavením souboru v Průzkumníku řešení projektu](../vsto/media/installshield-projectassistant.png "Project Assistant souboru v Průzkumníku řešení")  

2. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

3. V dolní části **Pomocník projektu** zvolte **soubory aplikace** tlačítko, které ukazuje následující obrázek.  

   ![Tlačítko soubory aplikace. ](../vsto/media/installshield-applicationfiles.png "Tlačítko soubory aplikace.")  

4. V **soubory aplikace** zvolte **přidat výstupy projektu** tlačítko.  

5. V **selektor výstupu Visual Studio** dialogové okno, vyberte **primární výstup** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  


## <a name="AddD"></a>Přidejte manifesty nasazení a aplikace  

###  
1. V **soubory aplikace** zvolte **přidat soubory** tlačítko.  

2. V **otevřít** dialogové okno, přejděte k adresáři výstupu **ExcelAddIn** projektu.  

   Výstupní adresář je obvykle **bin\release** podsložky kořenového adresáře projektu, v závislosti na konfiguraci sestavení, kterou zvolíte.  

3. Ve výstupním adresáři zvolte **ExcelAddIn.vsto** a **ExcelAddIn.dll.manifest** soubory a klikněte na tlačítko **otevřít** tlačítko.  

   **Soubory aplikace** stránka nyní obsahuje výstupní soubor projektu, manifest nasazení a manifest aplikace, jako ukazuje následující obrázek.  

   ![Výstupní soubory projektu instalace. ](../vsto/media/installshield-outputfiles.png "Výstupních souborů projektu instalace.")  


## <a name="Configure"></a>Konfigurace závislých součástí jako předpokladů  
Váš instalační program musí obsahovat nejen následující součásti, ale také všechny ostatní součásti, které jsou požadovány pro spuštění řešení.  


- Verze rozhraní .NET Framework, která cílová pro řešení Office.  

- Microsoft Visual Studio 2010 Tools for Office Runtime.  


### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Přidání rozhraní .NET Framework 4 nebo .NET Framework 4.5 jako předpokladu  

1. V **Průzkumníka řešení**, rozbalte **OfficeAddInSetup** uzel projektu, rozbalte **zadat Data aplikace** uzel a klikněte na tlačítko  **Distribuovatelné součásti** soubor, který ukazuje následující obrázek.  

   ![Distribuovatelné součásti souboru v Průzkumníku řešení](../vsto/media/installshield-redistributablesfile.png "The Redistribuovatelnost souboru v Průzkumníku řešení")  

2. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

   **Redistribuovatelnost** otevře se stránka.  

3. V seznamu distribuovatelných součástí označte příslušné zaškrtávací políčko pro verzi rozhraní .NET Framework, která vaše řešení cílí.  

   Například pokud vaše řešení cílí [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vyberte **Microsoft .NET Framework 4.5 Full** zaškrtávací políčko. Může zobrazit dialogové okno s dotazem, jestli chcete nainstalovat distribuovatelnou komponentu, kterou program InstallShield vyžaduje před přidáním komponenty jako předpokladu. Pokud se toto dialogové okno nezobrazí, součást již existuje ve vašem počítači.  

4. Pokud se zobrazí toto dialogové okno, vyberte **ne** tlačítko.  


### <a name="AddToolsForOffice"></a>Přidejte nástroje Visual Studio 2010 Tools for Office Runtime  
**Redistribuovatelnost** stránka obsahuje položku s názvem **Microsoft VSTO 2010 Runtime**, ale odkazuje na starší verzi modulu runtime. Proto může ručně vytvořit konfigurační soubor, který odkazuje na nejnovější verzi. Pak musíte umístit soubor do stejného adresáře jako konfigurační soubory pro všechny ostatní položky, které se zobrazují v **Redistribuovatelnost** stránky.  


#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Chcete-li přidat Visual Studio 2010 Tools for Office runtime jako předpoklad  

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

2. Generování identifikátoru GUID v sadě Visual Studio. Na **nástroje** nabídce zvolte **Create GUID**.  

3. V **GUID generator** programu, zvolte **formát registru** přepínač, zvolte **kopírování** tlačítko a klikněte na tlačítko **ukončovací** tlačítko.  

4. V programu Poznámkový blok nahraďte text **sem patří vaše GUID** vložením identifikátoru GUID na příslušné místo.  

   **&lt;Vlastnosti&gt;** element souboru se podobá následující.  


   ```xml  
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
   ```  

5. V řádku nabídek v programu Poznámkový blok, zvolte **souboru** > **Uložit**.  

6. V **uložit jako** dialogové okno, přejděte k vaší **Desktop** složky.  

7. V **uložit jako typ** klikněte na položku **všechny soubory (&#42;.&#42;)** .  

8. V **název_souboru** zadejte **Visual Studio 2010 Tools for Office Runtime.prq**a klikněte na tlačítko **Uložit** tlačítko.  

   > [!NOTE]  
   >    Ujistěte se, že přidáte **.prq** na konci názvu souboru pro identifikaci tohoto souboru jako souboru s předpokladem.  

9. Zavřete poznámkový blok.  

10. Z vaší **Desktop** složka, Kopírovat *Visual Studio 2010 Tools for Office Runtime.prq* souboru na jednu z následujících složek v počítači.  

   Pro 32bitové operační systémy: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites\\*  

   Pro 64bitové operační systémy: *% ProgramFiles (x86) %\2013LE\SetupPrerequisites\\*  

11. V **Redistributable** stránce projektu InstallShield klikněte na tlačítko **aktualizovat** tak aktualizujte seznam distribuovatelných součástí, jako je vidět na následujícím obrázku.  

   ![Tlačítko Aktualizovat. ](../vsto/media/installshield-refreshbutton.png "Tlačítko Aktualizovat.")  

12. V seznamu distribuovatelných součástí, vyberte **Visual Studio 2010 Tools for Office Runtime** zaškrtávací políčko.  

   Může otevřít dialogové okno s dotazem, jestli chcete nainstalovat distribuovatelnou komponentu. Pokud se toto dialogové okno nezobrazí, můžete přeskočit na [zadejte, kam chcete nasadit řešení na počítači uživatele](#Location) části tohoto tématu.  

13. Pokud se zobrazí toto dialogové okno, vyberte **ne** tlačítko.  


## <a name="Location"></a>Zadejte, kam chcete řešení nainstalovat na počítač uživatele  

1. V **Průzkumníka řešení**, rozbalte **OfficeAddInSetup** uzlu, rozbalte **uspořádání vašeho nastavení** uzel a klikněte na tlačítko **Obecnéinformace** souboru.  

2. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

3. V seznamu vlastností zvolte **Procházet** vedle **INSTALLDIR** vlastnost.  

4. V **nastavit INSTALLDIR** dialogového okna zvolte složku v počítači uživatele, ve kterém chcete nainstalovat řešení.  

   > [!NOTE]  
   >    Můžete také vytvořit podadresáře v **nastavit INSTALLDIR** dialogové okno tak, že otevřete místní nabídku pro libovolnou složku v seznamu.  


## <a name="ConfigureRegistry"></a>Konfigurace doplňku VSTO  
Můžete určit, zda chcete vašeho doplňku VSTO nainstalovat pro všechny uživatele počítače (počítač) nebo pouze pro uživatele provádějícího instalaci (za uživatele).  

Pokud chcete podporovat instalace pro jednotlivé počítače, vytvořte dva samostatné instalační programy. Můžete instalační programy lze rozdělit na základě verze Office (32bitová verze a 64bitová verze) nebo verze Windows (32bitová verze a 64bitová verze), na kterém běží uživatele.  

Uživatelské instalace vyžadují pouze jeden instalační program bez ohledu na verzi Office nebo Windows.  

> [!NOTE]  
> Tato část platí jenom v případě, že nasazujete doplňku VSTO. Pokud nasazujete přizpůsobení úrovni dokumentu, můžete okamžitě přejít na [konfigurace přizpůsobení na úrovni dokumentu](#ConfigureDocument) oddílu.  


### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Chcete-li určit, jestli chcete podporovat instalace pro jednotlivé uživatele nebo počítač  

1. V **Průzkumníka řešení**, rozbalte **OfficeAddInSetup** uzel projektu, rozbalte **uspořádat vlastní nastavení** uzel a klikněte na tlačítko **obecné informace**  souboru.  

2. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

   Vlastnosti projektu instalace se zobrazí.  

3. V seznamu **AllUSERS** vlastnost, určete, zda chcete toto řešení nainstalovat pro všechny uživatele počítače nebo pouze uživatele, který řešení nainstaluje.  

   Pro instalaci doplňku VSTO pro aktuálního uživatele, vyberte možnost **ALLUSERS = "" (instalace vázaná na uživatele)**. Pro instalaci doplňku VSTO pro všechny uživatele počítače, vyberte možnost **ALLUSERS = 1 (instalace vázaná na počítač)**  

   V dalším postupu vytvoříte klíče registru, které umožní aplikaci Office zjišťovat a načíst doplňku VSTO. Zobrazit [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  


### <a name="to-create-registry-keys"></a>Chcete-li vytvořit klíče registru  

1. V **Průzkumníka řešení**, zvolte **Project Assistant** uzlu.  

   V panelu nabídky zvolte **zobrazení** > **otevřít**.  

2. V dolní části **Pomocník projektu** zvolte **registr aplikace** tlačítko, které ukazuje následující obrázek.  

   ![Tlačítko aplikace registru. ](../vsto/media/installshield-applicationregistry.gif "Tlačítko registru aplikace.")  

   **Registr aplikace** se zobrazí stránka.  

3. V části **chcete konfigurovat data registru, který vaše aplikace bude instalovat?**, zvolte **Ano** přepínač.  

4. V **zobrazení registru cílového počítače** seznamu, přidejte klíč hierarchie, která umožňuje typ instalačního programu, kterou chcete vytvořit.  

   Cesta, kterou nakonfigurujete v této části závisí na tom, zda vytvoříte instalační program, který jednotlivé uživatele nebo instalační program, který jednotlivé počítače.  

   **Instalační program pro jednotlivé uživatele**  

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**  

   **Instalační programy pro jednotlivé počítače založené na verzi Office**  



| Verze Office<br /><br /> | Cesta konfigurace InstallShield<br /><br /> |
|----------------------------| - |
| 32bitová<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64bitových<br /><br /> | **HKEY_LOCAL_MACHINE\Software(64-Bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Instalační programy pro jednotlivé počítače založené na verzi Windows**  



| Verze Windows<br /><br /> | Cesta konfigurace InstallShield<br /><br /> |
|-----------------------------| - |
| 32bitová<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64bitových<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\Software(64-Bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]  
   >    Instalační program pro 64bitová verze Windows vyžaduje dvě cesty registru, protože je přípustný uživatelé budou spouštět 32bitové a 64bitové verze Office na počítači, na kterém běží 64bitová verze Windows.  

   > [!NOTE]  
   >    Jako osvědčený postup začněte název vašeho doplňku VSTO s názvem vaší společnosti. Tato úmluva se zvyšuje pravděpodobnost, že klíč bude jedinečný a snižuje pravděpodobnost konfliktu s doplňku VSTO od jiného dodavatele. Doplňky, které mají stejný název, například přepsat registrační klíče uživatele toho druhého. Tento přístup nemůže zaručit, že klíč bude jedinečný, ale může omezit potenciální kolize názvů.  

5. Po vytvoření hierarchie klíčů otevřete místní nabídku **SampleCompany.ExcelAddIn** klíče, zvolte **nový**a klikněte na tlačítko **řetězcovou hodnotu**.  

   Nová hodnota se zobrazí v **data registru cílového počítače** seznamu. Název hodnoty řetězce je zvýrazněn, takže můžete ji jakkoli přejmenovat.  

6. Hodnota, kterou chcete přejmenovat **popis**.  

7. Opakujte tento postup a vytvořte tak následující hodnoty.  



|Typ hodnoty<br /><br />|Název<br /><br />|  
|--------------|--------|  
|Řetězcová hodnota<br /><br />|**FriendlyName**<br /><br />|  
|Hodnota DWORD<br /><br />|**LoadBehavior**<br /><br />|  
|Řetězcová hodnota<br /><br />|**Manifest**<br /><br />|  

8. Otevřete místní nabídku **popis** hodnoty a klikněte na tlačítko **změnit**.  

   **Upravit Data** zobrazí se dialogové okno.  

9. V **údaj hodnoty** textové pole, zadejte **Excel Demo Add-In**a klikněte na tlačítko **OK** tlačítko.  

   Tento popis se zobrazí, když uživatel otevře aplikaci sady Office, otevře se **možnosti** dialogové okno a pak na **Add-Ins** podokně zvolí doplňku VSTO.  

10. Otevřete místní nabídku **FriendlyName** hodnoty a klikněte na tlačítko **změnit**.  

   **Upravit Data** zobrazí se dialogové okno.  

11. V **údaj hodnoty** textové pole, zadejte **Excel Demo Add-In**a klikněte na tlačítko **OK** tlačítko.  

   Tento řetězec je zobrazen v **doplňky modelu COM** dialogové okno v aplikaci Office. Výchozí hodnotou řetězce je ID doplňku VSTO  

12. Otevřete místní nabídku **LoadBehavior** hodnoty a klikněte na tlačítko **změnit**.  

   **Upravit Data** zobrazí se dialogové okno.  

13. V **údaj hodnoty** textové pole, zadejte **3**a klikněte na tlačítko **OK** tlačítko.  

   Hodnota 3 načte doplněk VSTO při spuštění aplikace. Další informace o hodnotách LoadBehavior naleznete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  

14. Otevřete místní nabídku **Manifest** hodnoty a klikněte na tlačítko **změnit**.  

   **Upravit Data** zobrazí se dialogové okno.  

15. V **údaj hodnoty** textové pole, zadejte **file:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal**a klikněte na tlačítko **OK** tlačítko.  

   Visual Studio 2010 Tools for Office Runtime používá tuto cestu k nalezení manifestu nasazení. **[INSTALLDIR]** část této cesty představuje makro, která se mapuje **INSTALLDIR** vlastnost **obecné informace** stránku vlastností projektu instalace programu InstallShield. Tato vlastnost určuje umístění na cílovém počítači pro instalaci doplňku VSTO. **| Vstolocal** přípona zajistí, že vaše řešení se načte z instalační složky, nikoli z mezipaměti ClickOnce.  

> [!IMPORTANT]  
> Pokud vytvoříte vlastní formulář regionu v doplňku VSTO pro Outlook, musíte vytvořit více položek registru pro registraci oblasti v aplikaci Outlook. Další informace najdete v tématu [oblastem formuláře položky registru pro aplikaci Outlook](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).  


## <a name="ConfigureDocument"></a>Konfigurace přizpůsobení na úrovni dokumentu  
Tato část platí jenom v případě, že nasazujete přizpůsobení na úrovni dokumentu. Pokud nasazujete doplňku VSTO, můžete přejít ihned na [sestavit projekt instalace](#Build) oddílu.  

Přizpůsobení na úrovni dokumentu nevyužívají klíče registru. Místo toho uživatelské vlastnosti dokumentu obsahují umístění manifestu nasazení.  

Chcete-li upravit vlastní vlastnosti, vytvořte program, který se odebere z dokumentu přizpůsobení úrovně dokumentu, změní příslušné vlastnosti a pak znovu vlastní nastavení dokumentu. Pak vytvoříte vlastní akci, která spustí program a přidáte tuto akci do projektu instalace.  

### <a name="to-create-a-program-that-modifies-document-properties"></a>Tvorba aplikací, které mění vlastnosti dokumentu  

1. V panelu nabídky zvolte **souboru** > **přidat** > **nový projekt**.  

   **Přidat nový projekt** zobrazí se dialogové okno.  

2. V podokně šablon, pod uzlem jazyku, který chcete použít, zvolte **Windows** složky.  

3. V seznamu typů projektů **Windows**, zvolte **konzolovou aplikaci** šablony.  

4. Pojmenujte projekt **SetExcelDocumentProperties**a klikněte na tlačítko **OK** tlačítko.  

5. V **Průzkumníka řešení**, zvolte **zobrazit všechny soubory** tlačítko, otevřete místní nabídku **SetExcelDocumentProperties** uzel projektu a klikněte na tlačítko **Přidat odkaz na**.  

6. V **správce odkazů** dialogového okna zvolte **rozšíření** kartu a potom zaškrtněte políčko u následujících sestavení a klikněte na tlačítko **OK** tlačítko.  


   - Microsoft.VisualStudio.Tools.Applications.Runtime  

   - Microsoft.VisualStudio.Tools.Applications.ServerDocument  

7. V **Průzkumníka řešení**, zvolte **Program.cs** souboru (pro aplikace C#) nebo **Module1.vb** souboru (pro aplikace Visual Basic).  

8. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

9. Nahraďte obsah celého souboru následujícím kódem.  

[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]  

10. Zkompilujte projekt.  


### <a name="to-add-a-custom-action-that-runs-your-program"></a>Chcete-li přidat vlastní akci, která spustí program  

1. V **Průzkumníka řešení**, rozbalte **OfficeAddInSetup** uzel projektu a klikněte na tlačítko **Project Assistant** soubor, který ukazuje následující obrázek.  

   ![Průvodce nastavením souboru v Průzkumníku řešení projektu](../vsto/media/installshield-projectassistant.png "Project Assistant souboru v Průzkumníku řešení")  

2. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

3. V dolní části **Pomocník projektu** zvolte **soubory aplikace** tlačítko, které ukazuje následující obrázek.  

   ![Tlačítko soubory aplikace. ](../vsto/media/installshield-applicationfiles.png "Tlačítko soubory aplikace.")  

4. V **soubory aplikace** zvolte **přidat výstupy projektu** tlačítko.  

   **Selektor výstupu Visual Studio** zobrazí se dialogové okno.  

5. V části **SetExcelDocumentProperties** uzlu, vyberte **primární výstup** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  

6. V **Průzkumníka řešení**v části **OfficeAddInSetup** uzlu, rozbalte **definovat požadavky na nastavení a akce** uzel a klikněte na tlačítko **vlastní Akce** složky.  

7. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

   V podokně na straně obrazovky se zobrazí seznam událostí.  

   > [!NOTE]  
   >    Pouze několik událostí, které se zobrazují v tomto seznamu jsou k dispozici v programu InstallShield Limited Edition. V tomto postupu spustíte program pomocí **dialogové okno po instalaci kompletní úspěch** událostí.  

8. V seznamu událostí v části **vlastní akce během instalace**, otevřete místní nabídku **dialogové okno po instalaci kompletní úspěch** události a klikněte na tlačítko **nového EXE**.  

   Vlastní akce, který je pojmenován **NewCustomAction1** se zobrazí v části **dialogové okno po instalaci kompletní úspěch** událostí. Sada vlastností pro vlastní akci se zobrazí v podokně vedle událostí.  

   > [!IMPORTANT]  
   >    Dvě **dialogové okno po instalaci kompletní úspěch** události se zobrazí v seznamu událostí. Ujistěte se, že jste zvolili instanci **dialogové okno po instalaci kompletní úspěch** událost, která se zobrazí v části **vlastní akce během instalace** uzlu.  

9. V seznamu **umístění zdroje** vlastnost, zvolte **nainstalovány s produktem**.  

10. Zvolte **Procházet** vedle **název_souboru** vlastnost.  

11. V **vyhledat cílový soubor** dialogové okno, přejděte na **SetExcelDocumentProperties.Primary.output** souboru a klikněte na tlačítko **otevřít** tlačítko.  

    Umístění tohoto souboru závisí na složku, která jste zadali pro **INSTALLDIR** vlastnost projektu instalace. Například pokud nastavíte tuto vlastnost na složku s názvem **[PersonalFolder] DemoWorkbookApp**, můžete najít **SetExcelDocumentProperties.Primary.output** soubor procházením **[ ProgramFilesFolder] \DemoWorkbookApp**.  

    V dalších několika krocích získáte ID řešení dokumentu a poté předáte toto ID jako parametr do konzolové aplikace. Také předáte umístění dokumentu, manifest nasazení a sestavení dokumentu.  

12. Otevřete místní nabídku **ExcelWorkbook** projektu a klikněte na tlačítko **otevřít složku v Průzkumníku Windows** nebo **otevřít složku v Průzkumníku souborů** v závislosti na vaší provozní systém.  

    Otevře se složka, která obsahuje vaše řešení.  

13. V poznámkovém bloku otevřete soubor řešení s projektem. Pro projekty jazyka Visual Basic je název souboru *ExcelWorkbook.vbproj*. Pro projekty jazyka C#, je název souboru *ExcelWorkbook.csproj*.  

14. V souboru projektu vyhledejte **&lt;SolutionID&gt;** elementu, zkopírujte jeho hodnotu do schránky a ukončete Poznámkový blok.  

    Tuto hodnotu lze předat do konzoly jako parametr.  

15. Na stránce vlastnosti **NewCustomAction1**, nastavte **příkazového řádku** vlastnost k následujícímu řádku textu.  


   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"  
   ```  

16. Nahraďte **vaše ID řešení** ID řešení, který jste zkopírovali do schránky.  

   > [!IMPORTANT]  
   >    Otestujte instalační program pro ověření, že konzolovou aplikaci, na kterém běží tato vlastní akce získat přístup k dokumentům v adresáři [INSTALLDIR]. Některé adresáře v počítači uživatele mohou vyžadovat přístup správce (například adresář Program Files). Pokud nasazujete řešení do adresáře, který vyžaduje přístup správce, měli byste otevřít **vlastnosti** dialogovému oknu *setup.exe* souboru, zvolte **kompatibility** kartu a potom vyberte **spustit tento program jako správce** zaškrtávací políčko, před distribucí instalačního programu. Pokud nechcete, aby uživatelé spouštěli instalační program s oprávněními správce, nastavte vlastnost [INSTALLDIR] na adresáře, ke kterému má uživatel pravděpodobně přístup již, jako **dokumenty** adresáře. Další informace najdete v tématu [zadejte ve které chcete řešení nainstalovat na počítač uživatele](#Location) části tohoto tématu.  


## <a name="Build"></a>Sestavit projekt instalace  

1. V **Průzkumníka řešení**, rozbalte **vydání** uzel a klikněte na tlačítko **vydání** souboru.  

2. V panelu nabídky zvolte **zobrazení** > **otevřít**.  

   **Sestavení** Průzkumník otevře v postranním podokně, ve kterém můžete zvolit typ verze, kterou chcete vytvořit.  

3. V **sestavení** explorer, zvolte **SingleImage** složky.  

4. V podokně vedle **sestavení** explorer, zvolte **Setup.exe** kartu.  

5. V **Setup.exe** stránku vlastností z **umístění požadavků InstallShield** klikněte na položku **stáhnout z webu**.  

6. V panelu nabídky zvolte **sestavení** > **nástroje Configuration Manager**.  

7. V **konfigurace aktivního řešení** klikněte na položku **SingleImage**.  

8. V **projektu kontexty** tabulku **konfigurace** sloupec **OfficeAddInSetup** projektu, zvolte **SingleImage**a pak Zvolte **Zavřít** tlačítko.  

9. V panelu nabídky zvolte **sestavení** > **sestavit OfficeAddInSetup**.  

   Po dokončení sestavení můžete najít *setup.exe* soubor **OfficeAddInSetup** projektu v následujícím umístění: <em>OfficeAddInSetupProjectRoot</em> **\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1\\**  


## <a name="see-also"></a>Viz také:  
[Požadavky řešení Office na nasazení](https://msdn.microsoft.com/library/9f672809-43a3-40a1-9057-397ce3b5126e)  
[Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
[Položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md)  
[Přehled přizpůsobených vlastností dokumentu](../vsto/custom-document-properties-overview.md)  
[Zajistit jeho důvěryhodnost do řešení pro systém Office](../vsto/granting-trust-to-office-solutions.md)  
[Zajistit jeho důvěryhodnost do dokumentů](../vsto/granting-trust-to-documents.md)  
[Nasazení Visual Studio 2010 Tools pro Office řešení pomocí Instalační služby systému Windows](http://go.microsoft.com/fwlink/?LinkId=201807)  
