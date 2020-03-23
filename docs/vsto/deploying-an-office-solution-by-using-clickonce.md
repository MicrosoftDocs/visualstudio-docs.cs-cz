---
title: Nasazení řešení Office pomocí ClickOnce
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416559"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Nasazení řešení Office pomocí ClickOnce
  Pokud použijete ClickOnce, můžete nasazení řešení Office v menším počtu kroků. Když publikujete aktualizace, vaše řešení je automaticky rozpozná a nainstaluje. Technologie ClickOnce ale vyžaduje, aby bylo řešení nainstalováno zvlášť pro každého uživatele počítače. Proto byste měli zvážit použití Instalační služby systému Windows (*.msi*), pokud více než jeden uživatel spustí vaše řešení ve stejném počítači.

## <a name="in-this-topic"></a>V tomto tématu

- [Publikování řešení](#Publish)

- [Rozhodněte se, jak chcete řešení udělit důvěryhodnost](#Trust)

- [Pomozte uživatelům nainstalovat řešení](#Helping)

- [Vložte dokument řešení do počítače koncového uživatele (pouze vlastní nastavení na úrovni dokumentu)](#Put)

- [Umístění dokumentu řešení na server se spuštěným SharePointem (jenom vlastní nastavení na úrovni dokumentu)](#SharePoint)

- [Vytvoření vlastního instalačního programu](#Custom)

- [Publikování aktualizace](#Update)

- [Změna umístění instalace řešení](#Location)

- [Vrácení řešení zpět na starší verzi](#Roll)

  Další informace o nasazení řešení Office vytvořením souboru Instalační služby systému Windows naleznete v [tématu Deploy a Office solution using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a>Publikování řešení
 Řešení můžete publikovat pomocí **Průvodce publikováním** nebo **Návrháře projektů**. V tomto postupu budete používat **Návrhář projektu,** protože poskytuje úplnou sadu možností publikování. Viz [Průvodce publikováním &#40;vývoj office v sadě Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Publikování řešení

1. V **Průzkumníku řešení**zvolte uzel, který je pojmenován pro váš projekt.

2. Na řádku nabídek zvolte **Project**, *ProjectName* **Properties**.

3. V **Návrháři projektu**zvolte kartu **Publikovat,** kterou znázorňuje následující obrázek.

    ![Karta Publikovat návrháře projektů](../vsto/media/vsto-publishtab.png "Karta Publikovat návrháře projektů")

4. Do pole **Umístění složky publikování (ftp server nebo cesta k souboru)** zadejte cestu ke složce, do které má **Návrhář projektu** kopírovat soubory řešení.

    Můžete zadat některý z následujících typů cest.

   - Místní cesta (například *C:\FolderName\FolderName*).

   - Cesta k jednotné úmluvě osn o pojmenování ke složce v síti (například * \\\Název_serveru\Název_složky).*

   - Relativní cesta (například *PublishFolder\\*, což je složka, do které je projekt ve výchozím nastavení publikován).

5. Do pole **Adresa URL instalační složky** zadejte plně kvalifikovanou cestu k umístění, kde koncoví uživatelé najdou vaše řešení.

    Pokud umístění ještě neznáte, do tohoto pole nic nezadávejte. Ve výchozím nastavení hledá technologie ClickOnce aktualizace ve složce, ze které uživatelé řešení instalují.

6. Zvolte tlačítko **Požadavky.**

7. V dialogovém okně **Požadavky** zkontrolujte, zda je zaškrtnuto políčko **Vytvořit instalační program k instalaci nezbytných součástí.**

8. V seznamu **Zvolit, které požadavky k instalaci** zaškrtněte, zaškrtněte políčka pro Instalační **službu systému Windows 4.5** a příslušný balíček rozhraní .NET Framework.

    Pokud například vaše řešení [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]cílí na program , zaškrtněte políčka u **Instalační služby systému Windows 4.5** a **Microsoft .NET Framework 4.5 Full**.

9. Pokud vaše řešení cílí na rozhraní .NET Framework 4.5, zaškrtněte také políčko **Visual Studio 2010 Tools for Office Runtime.**

    > [!NOTE]
    > Ve výchozím nastavení se toto políčko nezobrazí. Aby se toto zaškrtávací políčko zobrazilo, je nutné vytvořit balíček zaváděcího nástroje. Viz [Vytvoření balíčku zaváděcího nástroje pro doplněk VSTO pro Office 2013 s Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. V části **Zadejte umístění instalace pro požadavky**zvolte jednu z možností, které se zobrazí, a pak zvolte tlačítko **OK.**

     Jednotlivé možnosti jsou popsány v následující tabulce.

    |Možnost|Popis|
    |------------|-----------------|
    |**Stáhnout požadavky z webu dodavatele komponenty**|Uživatel bude vyzván, aby od dodavatele stáhl a nainstaloval nezbytné součásti.|
    |**Stáhnout požadavky ze stejného umístění jako moje aplikace**|Požadovaný software bude nainstalován spolu s řešením. Pokud zvolíte tuto možnost, sada Visual Studio za vás zkopíruje všechny požadované balíčky do umístění pro publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|
    |**Stáhnout požadavky z následujícího umístění**|Sada Visual Studio zkopíruje všechny balíčky požadovaných součástí do zadaného umístění a nainstaluje je společně s řešením.|

     Viz [dialogové okno Požadavky](../ide/reference/prerequisites-dialog-box.md).

11. Zvolte tlačítko **Aktualizace,** určete, jak často chcete, aby doplněk VSTO nebo vlastní nastavení každého koncového uživatele zkontroloval aktualizace, a pak zvolte tlačítko **OK.**

    > [!NOTE]
    > Pokud nasazujete pomocí disku CD nebo vyměnitelné jednotky, zvolte přepínač **Nikdy nekontrolovat aktualizace.**

     Informace o publikování aktualizace naleznete v [tématu Publikování aktualizace](#Update).

12. Zvolte tlačítko **Volby,** prohlédněte si volby v dialogovém okně **Možnosti** a pak zvolte tlačítko **OK.**

13. Zvolte tlačítko **Publikovat.**

     Sada Visual Studio přidá následující složky a soubory do složky pro publikování, kterou jste zadali v předchozím kroku tohoto postupu.

    - Složka **Soubory aplikace.**

    - Instalační program

    - Manifest nasazení, který odkazuje na manifest nasazení pro nejnovější verzi

      Složka **Soubory aplikace** obsahuje podsložku pro každou verzi, kterou publikujete. Jednotlivé podsložky pro konkrétní verzi obsahují následující soubory.

    - Manifest aplikace

    - Manifest nasazení

    - Sestavení přizpůsobení

      Následující obrázek znázorňuje strukturu složky publikování doplňku aplikace Outlook VSTO.

      ![Publikovat strukturu složek](../vsto/media/publishfolderstructure.png "Publikovat strukturu složek")

    > [!NOTE]
    > ClickOnce připojí rozšíření *.deploy* do sestavení tak, aby zabezpečená instalace Internetové informační služby (IIS) nezablokovala soubory z důvodu nebezpečného rozšíření. Když uživatel nainstaluje řešení, ClickOnce odebere *.deploy* rozšíření.

14. Zkopírujte soubory řešení do umístění instalace, které jste zadali v předchozím kroku tohoto postupu.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>Rozhodněte se, jak chcete řešení udělit důvěryhodnost
 Aby bylo možné řešení spustit v počítačích uživatelů, musíte buď zajistit jeho důvěryhodnost, nebo uživatelé musejí při instalaci řešení reagovat na výzvu k potvrzení jeho důvěryhodnosti. Pokud chcete zajistit důvěryhodnost řešení, podepište manifesty pomocí certifikátu, který určuje známého a důvěryhodného vydavatele. Viz [Důvěřovat řešení podpisem manifestů aplikace a nasazení](../vsto/granting-trust-to-office-solutions.md#Signing).

 Pokud nasazujete vlastní nastavení na úrovni dokumentu a chcete dokument umístit do složky v počítači uživatele nebo dokument zpřístupnit na sharepointovém webu, ujistěte se, že Office důvěřuje umístění dokumentu. Viz [Udělení důvěryhodnosti dokumentům](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>Pomozte uživatelům nainstalovat řešení
 Uživatelé mohou nainstalovat řešení spuštěním instalačního programu, otevřením manifestu nasazení nebo během vlastního nastavení na úrovni dokumentu a přímým otevřením dokumentu. Osvědčeným postupem je instalace řešení pomocí instalačního programu. Další dva přístupy nezajišťují, že je nainstalován nezbytný software. Pokud uživatelé chtějí otevřít dokument z umístění instalace, musejí jej přidat do seznamu důvěryhodných umístění v Centru zabezpečení aplikace Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Otevření dokumentu přizpůsobení na úrovni dokumentu
 Uživatelé mohou otevřít dokument přizpůsobení na úrovni dokumentu přímo z umístění instalace nebo tak, že dokument zkopírují do svého počítače a poté otevřou jeho místní kopii.

 Osvědčeným postupem je, že by uživatelé měli otevřít kopii dokumentu ve svém počítači, aby nemohla nastat situace, kdy se více uživatelů současně pokusí otevřít stejnou kopii. Pro vynucení tohoto postupu můžete nakonfigurovat instalační program tak, aby dokument zkopíroval do počítačů uživatelů. Viz [Vložte dokument řešení do počítače koncového uživatele (pouze vlastní nastavení na úrovni dokumentu).](#Put)

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Nainstalujte řešení otevřením manifestu nasazení z webu služby IIS
 Uživatelé mohou nainstalovat řešení pro Office tak, že z webu otevřou manifest nasazení. Zabezpečená instalace Internetové informační služby (IIS) však zablokuje soubory s příponou *.vsto.* Typ MIME musí být definován ve službě IIS před nasazením řešení pro Office pomocí služby IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Přidání typu MIME .vsto do služby IIS 6.0

1. Na serveru se službou IIS 6.0 zvolte **Spustit** > správce**internetové informační služby (IIS)****všechny nástroje pro** > **správu** >  programů .

2. Zvolte název počítače, složku **Webové servery** nebo web, který konfigurujete.

3. Na řádku nabídek zvolte**Vlastnosti** **akce** > .

4. Na kartě **Hlavičky HTTP** zvolte tlačítko **Typy MIME.**

5. V okně **Typy MIME** zvolte **tlačítko Nový.**

6. V okně **TYP MIME** zadejte **.vsto** jako rozšíření, zadejte **aplikaci/x-ms-vsto** jako typ MIME a potom použijte nové nastavení.

    > [!NOTE]
    > Aby se změny projevily, je nutné restartovat službu Publikování na webu nebo počkat na recyklaci pracovního procesu. Potom je nutné vyprázdnit diskovou mezipaměť prohlížeče a potom se pokusit znovu otevřít soubor *.vsto.*

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Přidání typu .vsto MIME do iis 7.0

1. Na serveru se službou IIS 7.0 zvolte **Spustit** > **příslušenství****Pro všechny programy** > .

2. Otevřete místní nabídku **příkazového řádku**a pak zvolte **Spustit jako správce.**

3. Do pole **Otevřít** zadejte následující cestu a pak zvolte tlačítko **OK.**

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Zadejte následující příkaz a poté použijte nová nastavení.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Aby se změny projevily, je nutné restartovat službu Publikování na webu nebo počkat na recyklaci pracovního procesu. Potom je nutné vyprázdnit diskovou mezipaměť prohlížeče a potom se pokusit znovu otevřít soubor *.vsto.*

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>Vložte dokument řešení do počítače koncového uživatele (pouze vlastní nastavení na úrovni dokumentu)
 Dokument řešení můžete zkopírovat do počítače koncového uživatele vytvořením akce po nasazení. Tímto způsobem uživatel nemusí ručně kopírovat dokument z umístění instalace do svého počítače po instalaci řešení. Budete muset vytvořit třídu, která definuje akci po nasazení, sestavení a publikování řešení, upravit manifest aplikace a znovu podepsat manifest aplikace a nasazení.

 Následující postupy předpokládají, že název projektu je **ExcelWorkbook** a že publikujete řešení do vytvořené složky s názvem **C:\publish** v počítači.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Vytvoření třídy, která definuje akci po nasazení

1. Na řádku nabídek zvolte Přidat nový**Add** > **projekt** **.** > 

2. V dialogovém okně **Přidat nový projekt** zvolte v podokně **Nainstalované šablony** složku **Windows.**

3. V podokně **Šablony** zvolte šablonu **Knihovna tříd.**

4. Do pole **Název** zadejte **FileCopyPDA**a pak zvolte tlačítko **OK.**

5. V **Průzkumníku řešení**zvolte projekt **FileCopyPDA.**

6. Na řádku nabídek zvolte **Project** > **Add Reference**.

7. Na kartě **.NET** přidejte `Microsoft.VisualStudio.Tools.Applications.Runtime` `Microsoft.VisualStudio.Tools.Applications.ServerDocument`odkazy na a .

8. Přejmenujte třídu na `FileCopyPDA`a nahraďte obsah souboru kódem. Tento kód provádí následující úlohy:

   - Zkopíruje dokument na plochu uživatele.

   - Změní vlastnost _AssemblyLocation z relativní cesty na plně kvalifikovanou cestu pro manifest nasazení.

   - Odstraní soubor, pokud uživatel řešení odinstaluje.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Sestavení a publikování řešení

1. V **Průzkumníku řešení**otevřete místní nabídku projektu **FileCopyPDA** a pak zvolte **Build**.

2. Otevřete místní nabídku pro projekt **ExcelWorkbooku** a pak zvolte **Sestavit**.

3. Otevřete místní nabídku pro projekt **ExcelWorkbooku** a pak zvolte **Přidat odkaz**.

4. V dialogovém okně **Přidat odkaz** zvolte kartu **Projekty,** zvolte **FileCopyPDA**a pak zvolte tlačítko **OK.**

5. V **Průzkumníku řešení**zvolte projekt **ExcelWorkbook.**

6. Na řádku nabídek zvolte **Project** > **New Folder**.

7. Zadejte **data**a pak zvolte klávesu **Enter.**

8. V **Průzkumníku řešení**zvolte složku **Data.**

9. Na řádku nabídek zvolte Přidat**existující položku** **projektu** > .

10. V dialogovém okně **Přidat existující položku** přejděte do výstupního adresáře pro projekt **ExcelWorkbook,** zvolte soubor **ExcelWorkbook.xlsx** a pak zvolte tlačítko **Přidat.**

11. V **Průzkumníku řešení** zvolte soubor **ExcelWorkbook.xlsx.**

12. V okně **Vlastnosti** změňte vlastnost **Akce sestavení** na **Obsah** a vlastnost Kopírovat **do výstupního adresáře** na **Kopírovat, pokud je novější**.

     Po dokončení těchto kroků bude projekt vypadat na následujícím obrázku.

     ![Struktura projektu akce po nasazení.](../vsto/media/vsto-postdeployment.png "Struktura projektu akce po nasazení.")

13. Publikování projektu **ExcelWorkbook.**

### <a name="modify-the-application-manifest"></a>Úprava manifestu aplikace

1. Otevřete adresář řešení **c:\publish**pomocí **Průzkumníka souborů**.

2. Otevřete složku **Soubory aplikací** a otevřete složku, která odpovídá nejnovější publikované verzi vašeho řešení.

3. Otevřete soubor **ExcelWorkbook.dll.manifest** v textovém editoru, jako je Poznámkový blok.

4. Za `</vstav3:update>` prvek přidejte následující kód. Pro atribut třídy `<vstav3:entryPoint>` prvku použijte následující syntaxi: *NamespaceName.ClassName*. V následujícím příkladu jsou názvy oborů názvů a tříd stejné, `FileCopyPDA.FileCopyPDA`takže výsledný název vstupního bodu je .

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>Opětovné podepsání aplikace a manifestů nasazení

1. Ve složce **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook zkopírujte** soubor certifikátu **ExcelWorkbook_TemporaryKey.pfx** a vložte jej do složky *PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion._

2. Otevřete příkazový řádek sady Visual Studio a změňte adresáře na složku **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ (například **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).

3. Podepište upravený manifest aplikace spuštěním následujícího příkazu:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Zobrazí se zpráva „ExcelWorkbook.dll.manifest successfully signed“ („Soubor ExcelWorkbook.dll.manifest byl úspěšně podepsán.“).

4. Změňte na složku **c:\publish** a potom aktualizujte a podepište manifest nasazení spuštěním následujícího příkazu:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > V předchozím příkladu nahraďte MostRecentVersionNumber číslem verze naposledy publikované verze řešení (například **1_0_0_4**).

     Zobrazí se zpráva „ExcelWorkbook.vsto successfully signed“ („Soubor ExcelWorkbook.vsto byl úspěšně podepsán.“).

5. Zkopírujte soubor *ExcelWorkbook.vsto* do adresáře **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber._

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Umístění dokumentu řešení na server se spuštěným SharePointem (jenom vlastní nastavení na úrovni dokumentu)
 Přizpůsobení na úrovni dokumentu můžete pro koncové uživatele publikovat pomocí služby SharePoint. Když uživatelé přejdou na web služby SharePoint a dokument otevřou, modul runtime automaticky nainstaluje řešení ze sdílené síťové složky do místního počítače uživatele. Jakmile je řešení nainstalováno místně, bude přizpůsobení nadále fungovat i v případě, že je dokument zkopírován do jiného umístění, například na plochu.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Umístění dokumentu na server, na kterém je spuštěna služba SharePoint

1. Přidejte dokument řešení do knihovny dokumentů na webu služby SharePoint.

2. Proveďte jeden z následujících postupů:

    - Pomocí konfiguračního nástroje sady Office přidejte server, na němž je spuštěna služba SharePoint, do Centra zabezpečení v aplikaci Word nebo Excel na všech počítačích uživatelů.

         Viz [Zásady a nastavení zabezpečení v Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Postarejte se, aby každý uživatel provedl následující kroky.

        1. Na místním počítači otevřete Word nebo Excel, zvolte kartu **Soubor** a pak zvolte tlačítko **Možnosti.**

        2. V dialogovém okně **Centrum zabezpečení** zvolte tlačítko **Důvěryhodná umístění.**

        3. Zaškrtněte **políčko Povolit důvěryhodná umístění v síti (nedoporučuje se)** a pak zvolte tlačítko **Přidat nové umístění.**

        4. Do pole **Cesta** zadejte adresu URL knihovny dokumentů SharePointu, která obsahuje *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*dokument, který jste nahráli (například ).

             Nepřidávejte název výchozí webové stránky, například *default.aspx* nebo *AllItems.aspx*.

        5. Zaškrtněte **políčko Podsložky tohoto umístění a** pak zvolte tlačítko **OK.**

             Když uživatelé otevřou dokument z webu služby SharePoint, dokument se otevře a nainstaluje se přizpůsobení. Uživatelé mohou dokument zkopírovat na svou plochu. Přizpůsobení bude stále možné spustit, protože vlastnosti v dokumentu odkazují na síťové umístění dokumentu.

## <a name="create-a-custom-installer"></a><a name="Custom"></a>Vytvoření vlastního instalačního programu
 Pro řešení Office můžete vytvořit vlastní instalační program namísto instalačního programu, který je pro vás vytvořen při publikování řešení. Můžete například použít přihlašovací skript ke spuštění instalace nebo můžete použít dávkový soubor k instalaci řešení bez interakce s uživatelem. Tyto scénáře fungují nejlépe, pokud jsou požadované součásti již nainstalovány v počítačích koncových uživatelů.

 V rámci vlastního procesu instalace volejte instalační nástroj pro řešení sady Office (*VSTOInstaller.exe*), který je ve výchozím nastavení nainstalován v následujícím umístění:

 *%commonprogramfiles%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Pokud nástroj není v tomto umístění, můžete k nalezení cesty k tomuto nástroji najít cestu k tomuto nástroji pomocí **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\VSTO Runtime Setup\v4\InstallerPath** Path nebo **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath.**

 Následující parametry můžete použít s *programem VSTOinstaller.exe*.

| Parametr | Definice |
|------------------| - |
| /Install nebo /I | Nainstaluje řešení. Za tímto parametrem musí následovat cesta k manifestu nasazení. Můžete určit cestu v místním počítači, univerzální složky konvence osn (UNC). Můžete zadat místní cestu (*C:\FolderName\PublishFolder*), relativní cestu (*Publikovat)\\*nebo plně kvalifikované umístění (*\\\Název__serveru\Název_složky* nebo<em>http://__ název__ _složky_složky).</em> |
| /Uninstall nebo /U | Odinstaluje řešení. Za tímto parametrem musí následovat cesta k manifestu nasazení. Můžete určit cestu může být v místním počítači, sdílené složky UNC. Můžete zadat místní cestu (*c:\FolderName\PublishFolder*), relativní cestu (*Publikovat)\\*nebo plně kvalifikované umístění (*\\\ServerName\FolderName* nebo<em>http://___ název__ _složky_složky).</em> |
| /Silent nebo /S | Při instalaci nebo odinstalaci se uživatelům nebudou zobrazovat výzvy k zadání vstupu ani žádné jiné zprávy. Pokud je vyžadována výzva k důvěře, vlastní nastavení není nainstalováno nebo aktualizováno. |
| /Help nebo /? | Zobrazí informace nápovědy. |

 Při spuštění souboru *VSTOinstaller.exe*se mohou zobrazit následující kódy chyb.

|Kód chyby|Definice|
|----------------|----------------|
|0|Řešení bylo úspěšně nainstalováno či odinstalováno nebo se zobrazila nápověda nástroje VSTOInstaller.|
|-100|Jedna nebo více možností příkazového řádku není platná nebo byla nastavena více než jednou. Další informace získáte zadáním "vstoinstaller /?" nebo [najdete v tématu Vytvoření vlastního instalačního programu pro řešení ClickOnce Office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Jedna nebo více možností příkazového řádku není platné. Pokud chcete získat další informace, zadejte příkaz "vstoinstaller /?".|
|-200|Identifikátor URI manifestu nasazení není platný. Pokud chcete získat další informace, zadejte příkaz "vstoinstaller /?".|
|-201|Řešení nelze nainstalovat, protože manifest nasazení není platný. Viz [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Řešení nelze nainstalovat, protože část Visual Studio Tools for Office manifestu aplikace není platná. Viz [Manifesty aplikací pro řešení Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Řešení nelze nainstalovat, protože došlo k chybě stahování. Zkontrolujte identifikátor URI nebo síťové umístění souboru manifestu nasazení a akci opakujte.|
|-300|Řešení nelze nainstalovat, protože došlo k výjimce zabezpečení. Viz [Řešení Secure Office](../vsto/securing-office-solutions.md).|
|-400|Řešení nelze nainstalovat.|
|-401|Řešení nelze odinstalovat.|
|-500|Operace byla zrušena, protože řešení nelze nainstalovat nebo odinstalovat nebo nelze stáhnout manifest nasazení.|

## <a name="publish-an-update"></a><a name="Update"></a>Publikování aktualizace
 Chcete-li aktualizovat řešení, publikujte jej znovu pomocí **Návrháře projektu** nebo **Průvodce publikováním**a potom zkopírujte aktualizované řešení do umístění instalace. Při kopírování souborů do umístění instalace je nutné přepsat předchozí soubory.

 Při příštím hledání aktualizace řešení vyhledá a načte novou verzi automaticky.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>Změna umístění instalace řešení
 Po publikování řešení můžete přidat nebo změnit cestu instalace. Změnit cestu instalace může být vhodné z některého z následujících důvodů:

- Instalační program byl zkompilován ještě předtím, než byla známa cesta instalace.

- Soubory řešení byly zkopírovány do jiného umístění.

- Změnil se název nebo umístění serveru, který hostuje instalační soubory.

  Pokud chcete pro řešení změnit cestu instalace, je nutné aktualizovat instalační program, který poté uživatelé musejí spustit. V případě přizpůsobení na úrovni dokumentu musejí uživatelé také aktualizovat vlastnost v dokumentu tak, aby odkazovala na nové umístění.

> [!NOTE]
> Pokud nechcete uživatele žádat o aktualizaci vlastností dokumentu, můžete požádat uživatele, aby aktualizovaný dokument získali z umístění instalace.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Změna cesty instalace v instalačním programu

1. Otevřete okno **příkazového řádku** a změňte adresáře do instalační složky.

2. Spusťte instalační program `/url` a zahrňte parametr, který přebírá novou instalační cestu jako řetězec.

    Následující příklad ukazuje, jak změnit cestu instalace na umístění na webu společnosti Fabrikam. Tuto adresu URL můžete nahradit požadovanou cestou:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Pokud se zobrazí zpráva, že bude zrušena platnost podpisu spustitelného souboru, znamená to, že certifikát, pomocí něhož bylo řešení podepsáno, již není platný a vydavatel je neznámý. V důsledku toho budou uživatelé muset před instalací řešení potvrdit, že zdroj řešení považují za důvěryhodný.

   > [!NOTE]
   > Chcete-li zobrazit aktuální hodnotu `setup.exe /url`adresy URL, spusťte .

   U vlastních nastavení na úrovni dokumentu musí uživatelé dokument otevřít a potom aktualizovat jeho _AssemblyLocation vlastnost. To mohou uživatelé provést pomocí následujícího postupu.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Aktualizace vlastnosti _AssemblyLocation v dokumentu

1. Na kartě **Soubor** zvolte **Informace**, které jsou znázorněny na následujícím obrázku.

     ![Karta Informace v Excelu](../vsto/media/vsto-infotab.png "Karta Informace v Excelu")

2. V seznamu **Vlastnosti** zvolte **Upřesnit vlastnosti**, které znázorňují následující obrázek.

     ![Rozšířené vlastnosti v aplikaci Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Rozšířené vlastnosti v aplikaci Excel.")

3. Na kartě **Vlastní** v seznamu **Vlastnosti** zvolte _AssemblyLocation, jak ukazuje následující obrázek.

     ![AssemblyLocation vlastnost.](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation vlastnost.")

     Pole **Hodnota** obsahuje identifikátor manifestu nasazení.

4. Před identifikátorzadejte plně kvalifikovanou cestu dokumentu následovanou pruhem do formátu *Path*|*Identifier* (například *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Další informace o formátování tohoto identifikátoru naleznete v [tématu Přehled vlastností vlastního dokumentu](../vsto/custom-document-properties-overview.md).

5. Zvolte tlačítko **OK** a pak dokument uložte a zavřete.

6. Nainstalujte řešení do zadaného umístění tak, že spustíte instalační program bez parametru /url.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>Vrácení řešení zpět na starší verzi
 Když vrátíte řešení zpět, budou uživatelé opět používat předchozí verzi tohoto řešení.

#### <a name="to-roll-back-a-solution"></a>Vrácení řešení zpět

1. Otevřete umístění instalace řešení.

2. Ve složce publikování nejvyšší úrovně odstraňte manifest nasazení (soubor *.vsto).*

3. Vyhledejte podsložku pro verzi, kterou chcete vrátit zpět.

4. Zkopírujte manifest nasazení z této podsložky do složky na nejvyšší úrovni.

     Chcete-li například vrátit zpět řešení, které se nazývá **OutlookAddIn1** z verze 1.0.0.1 na verzi 1.0.0.0, zkopírujte soubor **OutlookAddIn1.vsto** ze složky **OutlookAddIn1_1_0_0_0.** Vložte soubor do složky publikování nejvyšší úrovně a převezte manifest nasazení specifického pro verzi pro **OutlookAddIn1_1_0_0_1,** který již existoval.

     Následující ilustrace znázorňuje strukturu složky pro publikování v tomto příkladu.

     ![Publikovat strukturu složek](../vsto/media/publishfolderstructure.png "Publikovat strukturu složek")

     Až uživatel příště otevře aplikaci nebo upravený dokument, bude detekována změna manifestu nasazení. Předchozí verze řešení pro Office se spustí z mezipaměti technologie ClickOnce.

> [!NOTE]
> Místní data jsou uložena pouze pro jednu předchozí verzi řešení. Pokud vrátíte zpět dvě verze, místní data se nezachovají. Další informace o místních datech naleznete [v tématu Přístup k místním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Viz také

- [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)
- [Publikování řešení Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Postup: Publikování řešení Office pomocí clickonce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Postup: Instalace řešení ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Postup: Publikování řešení Office na úrovni dokumentu na sharepointovém serveru pomocí clickonce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Vytvoření vlastního instalačního programu pro řešení clickonce office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)