---
title: Nasazení řešení Office pomocí technologie ClickOnce
description: Přečtěte si, jak můžete nasadit řešení pro Office v méně krocích, pokud používáte ClickOnce. Když publikujete aktualizace, vaše řešení je automaticky rozpozná a nainstaluje.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d808348528a64cc184c7a6c50359c057b2325a75
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845645"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Nasazení řešení Office pomocí technologie ClickOnce
  Pokud používáte ClickOnce, můžete řešení pro Office nasadit v méně krocích. Když publikujete aktualizace, vaše řešení je automaticky rozpozná a nainstaluje. Technologie ClickOnce ale vyžaduje, aby bylo řešení nainstalováno zvlášť pro každého uživatele počítače. Proto byste měli zvážit použití Instalační služba systému Windows (*. msi*), pokud vaše řešení bude spouštět více než jeden uživatel ve stejném počítači.

## <a name="in-this-topic"></a>V tomto tématu

- [Publikování řešení](#Publish)

- [Rozhodněte, jak chcete tomuto řešení důvěřovat.](#Trust)

- [Pomáhat uživatelům s instalací řešení](#Helping)

- [Umístění dokumentu řešení do počítače koncového uživatele (pouze přizpůsobení na úrovni dokumentu)](#Put)

- [Umístění dokumentu řešení na server, na kterém je spuštěna služba SharePoint (pouze přizpůsobení na úrovni dokumentu)](#SharePoint)

- [Vytvoření vlastního instalačního programu](#Custom)

- [Publikování aktualizace](#Update)

- [Změna umístění instalace řešení](#Location)

- [Vrácení řešení zpět na předchozí verzi](#Roll)

  Další informace o tom, jak nasadit řešení pro Office vytvořením souboru Instalační služba systému Windows, najdete v tématu [nasazení řešení Office pomocí Instalační služba systému Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a> Publikování řešení
 Řešení můžete publikovat pomocí **Průvodce publikováním** nebo **Návrháře projektu**. V tomto postupu použijete **Návrháře projektu** , protože poskytuje kompletní sadu možností publikování. [V tématu Průvodce publikováním &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Publikování řešení

1. V **Průzkumník řešení** vyberte uzel s názvem pro váš projekt.

2. V panelu nabídek vyberte **projekt**, **vlastnosti** *ProjectName* .

3. V **Návrháři projektu** klikněte na kartu **publikovat** , která je znázorněna na následujícím obrázku.

    ![Karta publikovat v Návrháři projektu](../vsto/media/vsto-publishtab.png "Karta publikovat v Návrháři projektu")

4. Do pole **umístění složky pro publikování (server FTP nebo cesta k souboru)** zadejte cestu ke složce, do které chcete, aby **Návrhář projektu** kopíroval soubory řešení.

    Můžete zadat některý z následujících typů cest.

   - Místní cesta (například *C:\FolderName\FolderName*).

   - Cesta UNC (Uniform Naming Convention) ke složce v síti (například *\\ \ServerName\FolderName*).

   - Relativní cesta (například *PublishFolder \\*, což je složka, do které je projekt publikován ve výchozím nastavení).

5. Do pole **Adresa URL instalační složky** zadejte plně kvalifikovanou cestu k umístění, kde budou koncoví uživatelé hledat vaše řešení.

    Pokud umístění ještě neznáte, nezadávejte do tohoto pole nic. Ve výchozím nastavení hledá technologie ClickOnce aktualizace ve složce, ze které uživatelé řešení instalují.

6. Klikněte na tlačítko **požadavky** .

7. V dialogovém okně **předpoklady** ověřte, zda je zaškrtnuto políčko **vytvořit instalační program pro instalaci požadovaných součástí** .

8. V seznamu **zvolte požadované součásti pro instalaci** zaškrtněte políčka **Instalační služba systému Windows 4,5** a příslušné .NET Framework balíčku.

    Například pokud vaše řešení cílí na [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , zaškrtněte políčka **Instalační služba systému Windows 4,5** a **Microsoft .NET Framework 4,5 Full**.

9. Pokud vaše řešení cílí na .NET Framework 4,5, zaškrtněte také políčko **Visual Studio 2010 Tools for Office runtime** .

    > [!NOTE]
    > Ve výchozím nastavení se toto zaškrtávací políčko nezobrazí. Aby se toto zaškrtávací políčko zobrazilo, je nutné vytvořit balíček zaváděcího nástroje. Další informace najdete v tématu [Vytvoření balíčku zaváděcího nástroje pro doplněk VSTO Office 2013 s Visual studiem 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. V části **Zadejte umístění instalace pro požadované součásti** zvolte jednu z možností, které se zobrazí, a pak klikněte na tlačítko **OK** .

     Jednotlivé možnosti jsou popsány v následující tabulce.

    |Možnost|Popis|
    |------------|-----------------|
    |**Stáhnout požadavky z webu dodavatele součásti**|Uživatel bude vyzván, aby od dodavatele stáhl a nainstaloval nezbytné součásti.|
    |**Stáhnout požadavky ze stejného umístění jako moje aplikace**|Požadovaný software bude nainstalován spolu s řešením. Pokud zvolíte tuto možnost, sada Visual Studio za vás zkopíruje všechny požadované balíčky do umístění pro publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|
    |**Stáhnout požadované součásti z následujícího umístění**|Sada Visual Studio zkopíruje všechny balíčky požadovaných součástí do zadaného umístění a nainstaluje je společně s řešením.|

     Zobrazí se [dialogové okno předpoklady](../ide/reference/prerequisites-dialog-box.md).

11. Klikněte na tlačítko **aktualizace** a určete, jak často chcete, aby každý doplněk VSTO nebo vlastní nastavení pro každého koncového uživatele kontroloval aktualizace, a pak klikněte na tlačítko **OK** .

    > [!NOTE]
    > Pokud nasazujete pomocí disku CD-ROM nebo vyměnitelné jednotky, klikněte na přepínač **nikdy Nekontrolovat aktualizace** .

     Informace o publikování aktualizace najdete v tématu [publikování aktualizace](#Update).

12. Klikněte na tlačítko **Možnosti** , zkontrolujte možnosti v dialogovém okně **Možnosti** a pak klikněte na tlačítko **OK** .

13. Klikněte na tlačítko **Publikovat nyní** .

     Sada Visual Studio přidá následující složky a soubory do složky pro publikování, kterou jste zadali v předchozím kroku tohoto postupu.

    - Složka **souborů aplikace**

    - Instalační program

    - Manifest nasazení, který odkazuje na manifest nasazení pro nejnovější verzi

      Složka **soubory aplikace** obsahuje podsložku pro každou verzi, kterou publikujete. Jednotlivé podsložky pro konkrétní verzi obsahují následující soubory.

    - Manifest aplikace

    - Manifest nasazení

    - Sestavení přizpůsobení

      Následující ilustrace znázorňuje strukturu složky pro publikování doplňku VSTO pro Outlook.

      ![Publikovat strukturu složek](../vsto/media/publishfolderstructure.png "Publikovat strukturu složek")

    > [!NOTE]
    > ClickOnce připojí rozšíření *. deploy* k sestavením, aby zabezpečená instalace služby Internetová informační služba (IIS) neblokovala soubory z důvodu nezabezpečeného rozšíření. Když uživatel toto řešení nainstaluje, ClickOnce odebere příponu *. deploy* .

14. Zkopírujte soubory řešení do umístění instalace, které jste zadali v předchozím kroku tohoto postupu.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> Rozhodněte, jak chcete tomuto řešení důvěřovat.
 Aby bylo možné řešení spustit v počítačích uživatelů, musíte buď zajistit jeho důvěryhodnost, nebo uživatelé musejí při instalaci řešení reagovat na výzvu k potvrzení jeho důvěryhodnosti. Pokud chcete zajistit důvěryhodnost řešení, podepište manifesty pomocí certifikátu, který určuje známého a důvěryhodného vydavatele. Přečtěte si téma [důvěřování řešení podpisem manifestů aplikace a nasazení](../vsto/granting-trust-to-office-solutions.md#Signing).

 Pokud nasazujete přizpůsobení na úrovni dokumentu a chcete dokument vložit do složky v počítači uživatele nebo ho zpřístupnit na webu služby SharePoint, ujistěte se, že Office důvěřuje umístění dokumentu. Viz [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> Pomáhat uživatelům s instalací řešení
 Uživatelé mohou řešení nainstalovat spuštěním instalačního programu, otevřením manifestu nasazení nebo během přizpůsobení na úrovni dokumentu otevření dokumentu přímo. Osvědčeným postupem je instalace řešení pomocí instalačního programu. Druhé dva přístupy nezajistí, že je nainstalovaný požadovaný software. Pokud uživatelé chtějí otevřít dokument z umístění instalace, musejí jej přidat do seznamu důvěryhodných umístění v Centru zabezpečení aplikace Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Otevření dokumentu přizpůsobení na úrovni dokumentu
 Uživatelé mohou otevřít dokument přizpůsobení na úrovni dokumentu přímo z umístění instalace nebo tak, že dokument zkopírují do svého počítače a poté otevřou jeho místní kopii.

 Osvědčeným postupem je, že by uživatelé měli otevřít kopii dokumentu ve svém počítači, aby nemohla nastat situace, kdy se více uživatelů současně pokusí otevřít stejnou kopii. Pro vynucení tohoto postupu můžete nakonfigurovat instalační program tak, aby dokument zkopíroval do počítačů uživatelů. Viz [umístění dokumentu řešení do počítače koncového uživatele (pouze přizpůsobení na úrovni dokumentu)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Nainstalujte řešení otevřením manifestu nasazení z webu služby IIS.
 Uživatelé mohou nainstalovat řešení pro Office tak, že z webu otevřou manifest nasazení. Zabezpečená instalace služby Internetová informační služba (IIS) ale bude blokovat soubory s příponou *. VSTO* . Typ MIME musí být definován ve službě IIS před nasazením řešení pro Office pomocí služby IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Přidání typu MIME .vsto do služby IIS 6.0

1. Na serveru, na kterém je spuštěná služba IIS 6,0, vyberte **Spustit**  >  **všechny programy**  >  **Administrative Tools**  >   **správce Internetová informační služba (IIS)**.

2. Vyberte název počítače, složku **webů** nebo web, který konfigurujete.

3. Na řádku nabídek klikněte na vlastnosti **Akce**  >  **Properties**.

4. Na kartě **hlavičky protokolu HTTP** klikněte na tlačítko **typy MIME** .

5. V okně **typy MIME** klikněte na tlačítko **Nový** .

6. V okně **typ MIME** zadejte **. VSTO** jako příponu, jako typ MIME zadejte **Application/x-MS-VSTO** a pak použijte nová nastavení.

    > [!NOTE]
    > Aby se změny projevily, je nutné restartovat službu Publikování na webu nebo počkat na recyklaci pracovního procesu. Pak musíte vyprázdnit mezipaměť disku prohlížeče a pak zkusit soubor *. VSTO* otevřít znovu.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Přidání typu MIME. VSTO do služby IIS 7,0

1. Na serveru, na kterém je spuštěná služba IIS 7,0, vyberte **Start**  >  **všechny programy**  >  **příslušenství**.

2. Otevřete místní nabídku **příkazového řádku** a pak zvolte možnost  **Spustit jako správce.**

3. Do pole **otevřít** zadejte následující cestu a pak klikněte na tlačítko **OK** .

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Zadejte následující příkaz a poté použijte nová nastavení.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Aby se změny projevily, je nutné restartovat službu Publikování na webu nebo počkat na recyklaci pracovního procesu. Pak musíte vyprázdnit mezipaměť disku prohlížeče a pak zkusit soubor *. VSTO* otevřít znovu.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> Umístění dokumentu řešení do počítače koncového uživatele (pouze přizpůsobení na úrovni dokumentu)
 Můžete zkopírovat dokument řešení do počítače koncového uživatele tím, že vytvoříte akci po nasazení. Uživatel tak nebude muset ručně kopírovat dokument z umístění instalace do svého počítače po instalaci vašeho řešení. Budete muset vytvořit třídu, která definuje akci po nasazení, sestavit a publikovat řešení, upravit manifest aplikace a znovu podepsat manifest aplikace a nasazení.

 Následující postupy předpokládají, že název projektu je **ExcelWorkbook** a že řešení publikujete do vytvořené složky s názvem **C:\publish** v počítači.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Vytvoření třídy, která definuje akci po nasazení

1. Na řádku nabídek klikněte na položku **soubor**  >  **Přidat**  >  **Nový projekt**.

2. V dialogovém okně **Přidat nový projekt** v podokně **Nainstalované šablony** vyberte složku **Windows** .

3. V podokně **šablony** vyberte šablonu **Knihovna tříd** .

4. Do pole **název** zadejte **FileCopyPDA** a poté klikněte na tlačítko **OK** .

5. V **Průzkumník řešení** vyberte projekt **FileCopyPDA** .

6. Na panelu nabídek vyberte **projekt**  >  **Přidat odkaz**.

7. Na kartě **.NET** přidejte odkazy na `Microsoft.VisualStudio.Tools.Applications.Runtime` a `Microsoft.VisualStudio.Tools.Applications.ServerDocument` .

8. Přejmenujte třídu na `FileCopyPDA` a poté nahraďte obsah souboru kódem. Tento kód provádí následující úlohy:

   - Zkopíruje dokument na plochu uživatele.

   - Změní vlastnost _AssemblyLocation z relativní cesty na plně kvalifikovanou cestu pro manifest nasazení.

   - Odstraní soubor, pokud uživatel řešení odinstaluje.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Sestavení a publikování řešení

1. V **Průzkumník řešení** otevřete místní nabídku pro projekt **FileCopyPDA** a pak zvolte možnost **sestavit**.

2. Otevřete místní nabídku pro projekt **ExcelWorkbook** a pak zvolte možnost **sestavit**.

3. Otevřete místní nabídku projektu **ExcelWorkbook** a poté zvolte možnost **Přidat odkaz**.

4. V dialogovém okně **Přidat odkaz** zvolte kartu **projekty** , zvolte možnost **FileCopyPDA** a pak klikněte na tlačítko **OK** .

5. V **Průzkumník řešení** vyberte projekt **ExcelWorkbook** .

6. Na panelu nabídek vyberte položku **projekt**  >  **Nová složka**.

7. Zadejte **data** a pak zvolte klávesu **ENTER** .

8. V **Průzkumník řešení** vyberte složku **data** .

9. Na panelu nabídek vyberte **projekt**  >  **Přidat existující položku**.

10. V dialogovém okně **Přidat existující položku** vyhledejte výstupní adresář pro projekt **ExcelWorkbook** , zvolte soubor **ExcelWorkbook.xlsx** a pak klikněte na tlačítko **Přidat** .

11. V **Průzkumník řešení** vyberte soubor **ExcelWorkbook.xlsx** .

12. V okně **vlastnosti** změňte vlastnost **Akce sestavení** na **obsah** a vlastnost **Kopírovat do výstupního adresáře** na **Kopírovat, pokud je novější**.

     Po dokončení těchto kroků bude projekt vypadat podobně jako na následujícím obrázku.

     ![Struktura projektu akce po nasazení.](../vsto/media/vsto-postdeployment.png "Struktura projektu akce po nasazení.")

13. Publikujte projekt **ExcelWorkbook** .

### <a name="modify-the-application-manifest"></a>Úprava manifestu aplikace

1. Pomocí **Průzkumníka souborů** otevřete adresář řešení, **c:\publish**.

2. Otevřete složku **soubory aplikace** a poté otevřete složku, která odpovídá nejnovější publikované verzi vašeho řešení.

3. Otevřete soubor **ExcelWorkbook.dll. manifest** v textovém editoru, jako je například Poznámkový blok.

4. Po `</vstav3:update>` elementu přidejte následující kód. Pro atribut class `<vstav3:entryPoint>` elementu použijte následující syntaxi: *Namespace. ClassName*. V následujícím příkladu jsou názvy oborů názvů a tříd stejné, takže výsledný název vstupního bodu je `FileCopyPDA.FileCopyPDA` .

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

1. Ve složce **%UserProfile%\Documents\Visual Studio 2013 \ Projects\ExcelWorkbook\ExcelWorkbook** zkopírujte soubor certifikátu **ExcelWorkbook_TemporaryKey. pfx** a vložte ho do složky *PublishFolder* **\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ .

2. Otevřete příkazový řádek sady Visual Studio a potom změňte adresáře na složku MostRecentPublishedVersion **Files\ExcelWorkbook pro c:\publish\Application** \_ _MostRecentPublishedVersion_ (například **soubory c:\publish\Application \ ExcelWorkbook_1_0_0_4**).

3. Podepište upravený manifest aplikace spuštěním následujícího příkazu:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Zobrazí se zpráva „ExcelWorkbook.dll.manifest successfully signed“ („Soubor ExcelWorkbook.dll.manifest byl úspěšně podepsán.“).

4. Přejděte do složky **c:\publish** a pak aktualizujte a podepište manifest nasazení spuštěním následujícího příkazu:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > V předchozím příkladu nahraďte MostRecentVersionNumber číslem verze naposledy publikované verze vašeho řešení (například **1_0_0_4**).

     Zobrazí se zpráva „ExcelWorkbook.vsto successfully signed“ („Soubor ExcelWorkbook.vsto byl úspěšně podepsán.“).

5. Zkopírujte soubor *ExcelWorkbook. VSTO* do adresáře **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentVersionNumber_ .

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a> Umístění dokumentu řešení na server, na kterém je spuštěna služba SharePoint (pouze přizpůsobení na úrovni dokumentu)
 Přizpůsobení na úrovni dokumentu můžete pro koncové uživatele publikovat pomocí služby SharePoint. Když uživatelé přejdou na web služby SharePoint a dokument otevřou, modul runtime automaticky nainstaluje řešení ze sdílené síťové složky do místního počítače uživatele. Jakmile je řešení nainstalováno místně, bude přizpůsobení nadále fungovat i v případě, že je dokument zkopírován do jiného umístění, například na plochu.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Umístění dokumentu na server, na kterém je spuštěna služba SharePoint

1. Přidejte dokument řešení do knihovny dokumentů na webu služby SharePoint.

2. Proveďte jeden z následujících postupů:

    - Pomocí konfiguračního nástroje sady Office přidejte server, na němž je spuštěna služba SharePoint, do Centra zabezpečení v aplikaci Word nebo Excel na všech počítačích uživatelů.

         Viz [zásady zabezpečení a nastavení v sadě Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Postarejte se, aby každý uživatel provedl následující kroky.

        1. V místním počítači otevřete Word nebo Excel, zvolte kartu **soubor** a pak klikněte na tlačítko **Možnosti** .

        2. V dialogovém okně **Centrum zabezpečení** klikněte na tlačítko **důvěryhodná umístění** .

        3. Zaškrtněte políčko pro **Povolení důvěryhodných umístění v síti (nedoporučuje se)** a pak klikněte na tlačítko **Přidat nové umístění** .

        4. Do pole **cesta** zadejte adresu URL knihovny dokumentů služby SharePoint, která obsahuje dokument, který jste odeslali (například *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             Nepřidávat název výchozí webové stránky, jako je například *Default. aspx* nebo *AllItems. aspx*.

        5. Zaškrtněte políčko **podsložky tohoto umístění je také důvěryhodné** a pak klikněte na tlačítko **OK** .

             Když uživatelé otevřou dokument z webu služby SharePoint, dokument se otevře a nainstaluje se přizpůsobení. Uživatelé mohou dokument zkopírovat na svou plochu. Přizpůsobení bude stále možné spustit, protože vlastnosti v dokumentu odkazují na síťové umístění dokumentu.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> Vytvoření vlastního instalačního programu
 Pro řešení Office můžete vytvořit vlastní instalační program místo použití instalačního programu, který jste vytvořili při publikování řešení. Pomocí skriptu pro přihlášení můžete například spustit instalaci, nebo můžete použít dávkový soubor k instalaci řešení bez zásahu uživatele. Tyto scénáře fungují nejlépe, pokud jsou požadované součásti již nainstalovány v počítačích koncových uživatelů.

 Jako součást vlastního procesu instalace zavolejte instalační nástroj pro řešení Office (*VSTOInstaller.exe*), který je ve výchozím nastavení nainstalovaný v následujícím umístění:

 *%COMMONPROGRAMFILES%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Pokud nástroj není v tomto umístění, můžete k vyhledání cesty k tomuto nástroji použít klíč registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** nebo **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** .

 Pomocí *VSTOinstaller.exe* můžete použít následující parametry.

| parametr | Definice |
|------------------| - |
| /Install nebo /I | Nainstaluje řešení. Za tímto parametrem musí následovat cesta k manifestu nasazení. Můžete zadat cestu v místním počítači, sdílenou složku UNC (Universal Naming Convention). Můžete zadat místní cestu (*C:\FolderName\PublishFolder*), relativní cestu (*\\ publikování*) nebo plně kvalifikované umístění (*\\ \ServerName\FolderName* nebo http://<em>servername/název_složky</em>). |
| /Uninstall nebo /U | Odinstaluje řešení. Za tímto parametrem musí následovat cesta k manifestu nasazení. Můžete zadat cestu v místním počítači, sdílenou složku ve formátu UNC. Můžete zadat místní cestu (*c:\FolderName\PublishFolder*), relativní cestu (*\\ publikování*) nebo plně kvalifikované umístění (*\\ \ServerName\FolderName* nebo http://<em>servername/název_složky</em>). |
| /Silent nebo /S | Při instalaci nebo odinstalaci se uživatelům nebudou zobrazovat výzvy k zadání vstupu ani žádné jiné zprávy. Pokud je vyžadováno zobrazení výzvy vztahu důvěryhodnosti, přizpůsobení není nainstalováno nebo aktualizováno. |
| /Help nebo /? | Zobrazí informace nápovědy. |

 Při spuštění *VSTOinstaller.exe* se mohou zobrazit následující chybové kódy.

|Kód chyby|Definice|
|----------------|----------------|
|0|Řešení bylo úspěšně nainstalováno či odinstalováno nebo se zobrazila nápověda nástroje VSTOInstaller.|
|-100|Jedna nebo více parametrů příkazového řádku není platná nebo byla nastavena více než jednou. Další informace získáte zadáním příkazu "VSTOInstaller/?". nebo si přečtěte téma [Vytvoření vlastního instalačního programu pro řešení ClickOnce pro sadu Office](/previous-versions/bb772078(v=vs.110)).|
|-101|Jedna nebo více parametrů příkazového řádku je neplatných. Pokud chcete získat další informace, zadejte příkaz "vstoinstaller /?".|
|-200|Identifikátor URI manifestu nasazení není platný. Pokud chcete získat další informace, zadejte příkaz "vstoinstaller /?".|
|-201|Řešení se nepovedlo nainstalovat, protože manifest nasazení není platný. Viz [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Řešení se nepovedlo nainstalovat, protože oddíl Visual Studio Tools for Office manifestu aplikace není platný. Podívejte se [na manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Řešení nelze nainstalovat, protože došlo k chybě při stahování. Zkontrolujte identifikátor URI nebo síťové umístění souboru manifestu nasazení a akci opakujte.|
|-300|Řešení se nepovedlo nainstalovat, protože došlo k výjimce zabezpečení. Viz [zabezpečení řešení pro Office](../vsto/securing-office-solutions.md).|
|-400|Řešení se nepovedlo nainstalovat.|
|-401|Řešení se nepovedlo odinstalovat.|
|-500|Operace byla zrušena, protože řešení nelze nainstalovat nebo odinstalovat nebo nelze stáhnout manifest nasazení.|

## <a name="publish-an-update"></a><a name="Update"></a> Publikování aktualizace
 Chcete-li aktualizovat řešení, znovu ho publikujete pomocí **Návrháře projektu** nebo **Průvodce publikováním** a poté zkopírujete aktualizované řešení do umístění instalace. Při kopírování souborů do umístění instalace je nutné přepsat předchozí soubory.

 Když řešení příště vyhledá aktualizaci, najde a automaticky načte novou verzi.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> Změna umístění instalace řešení
 Po publikování řešení můžete přidat nebo změnit cestu instalace. Změnit cestu instalace může být vhodné z některého z následujících důvodů:

- Instalační program byl zkompilován ještě předtím, než byla známa cesta instalace.

- Soubory řešení byly zkopírovány do jiného umístění.

- Změnil se název nebo umístění serveru, který hostuje instalační soubory.

  Pokud chcete pro řešení změnit cestu instalace, je nutné aktualizovat instalační program, který poté uživatelé musejí spustit. V případě přizpůsobení na úrovni dokumentu musejí uživatelé také aktualizovat vlastnost v dokumentu tak, aby odkazovala na nové umístění.

> [!NOTE]
> Pokud nechcete požádat uživatele, aby aktualizovali své vlastnosti dokumentu, můžete požádat uživatele, aby si z umístění instalace aktualizovali dokument.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Změna cesty instalace v instalačním programu

1. Otevřete okno **příkazového řádku** a potom změňte adresáře na instalační složku.

2. Spusťte instalační program a zahrňte `/url` parametr, který vezme novou cestu instalace jako řetězec.

    Následující příklad ukazuje, jak změnit cestu instalace na umístění na webu společnosti Fabrikam. Tuto adresu URL můžete nahradit požadovanou cestou:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Pokud se zobrazí zpráva, že bude zrušena platnost podpisu spustitelného souboru, znamená to, že certifikát, pomocí něhož bylo řešení podepsáno, již není platný a vydavatel je neznámý. V důsledku toho budou uživatelé muset před instalací řešení potvrdit, že zdroj řešení považují za důvěryhodný.

   > [!NOTE]
   > Chcete-li zobrazit aktuální hodnotu adresy URL, spusťte příkaz `setup.exe /url` .

   V případě přizpůsobení na úrovni dokumentu musí uživatelé otevřít dokument a následně aktualizovat jeho vlastnost _AssemblyLocation. To mohou uživatelé provést pomocí následujícího postupu.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Aktualizace vlastnosti _AssemblyLocation v dokumentu

1. Na kartě **soubor** vyberte možnost **informace**, která je znázorněna na následujícím obrázku.

     ![Karta informace v Excelu](../vsto/media/vsto-infotab.png "Karta informace v Excelu")

2. V seznamu **vlastnosti** vyberte možnost **upřesňující vlastnosti**, která je znázorněna na následujícím obrázku.

     ![Rozšířené vlastnosti v aplikaci Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Rozšířené vlastnosti v aplikaci Excel.")

3. Na kartě **vlastní** v seznamu **vlastnosti** vyberte možnost _AssemblyLocation, jak ukazuje následující obrázek.

     ![Vlastnost AssemblyLocation](../vsto/media/vsto-assemblylocationproperty.png "Vlastnost AssemblyLocation")

     Pole **hodnota** obsahuje identifikátor manifestu nasazení.

4. Před identifikátorem zadejte plně kvalifikovanou cestu k dokumentu následovaný pruhem v poli *Path* | *identifikátor* cesty formátu (například *File://servername/FolderName/filename|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Další informace o tom, jak tento identifikátor naformátovat, najdete v tématu [Přehled vlastností vlastního dokumentu](../vsto/custom-document-properties-overview.md).

5. Klikněte na tlačítko **OK** a pak dokument uložte a zavřete.

6. Nainstalujte řešení do zadaného umístění tak, že spustíte instalační program bez parametru /url.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> Vrácení řešení zpět na předchozí verzi
 Když vrátíte řešení zpět, budou uživatelé opět používat předchozí verzi tohoto řešení.

#### <a name="to-roll-back-a-solution"></a>Vrácení řešení zpět

1. Otevřete umístění instalace řešení.

2. Ve složce pro publikování na nejvyšší úrovni odstraňte manifest nasazení (soubor *. VSTO* ).

3. Vyhledejte podsložku pro verzi, kterou chcete vrátit zpět.

4. Zkopírujte manifest nasazení z této podsložky do složky na nejvyšší úrovni.

     Pokud například chcete vrátit řešení s názvem **OutlookAddIn1** z verze 1.0.0.1 na verzi 1.0.0.0, zkopírujte soubor **OutlookAddIn1. vsto** ze složky **OutlookAddIn1_1_0_0_0** . Vložte soubor do složky pro publikování na nejvyšší úrovni a přepíše manifest nasazení specifický pro verzi **OutlookAddIn1_1_0_0_1** , který již existuje.

     Následující ilustrace znázorňuje strukturu složky pro publikování v tomto příkladu.

     ![Publikovat strukturu složek](../vsto/media/publishfolderstructure.png "Publikovat strukturu složek")

     Až uživatel příště otevře aplikaci nebo upravený dokument, bude detekována změna manifestu nasazení. Předchozí verze řešení pro Office se spustí z mezipaměti technologie ClickOnce.

> [!NOTE]
> Místní data jsou uložena pouze pro jednu předchozí verzi řešení. Pokud vrátíte zpět dvě verze, místní data se nezachovají. Další informace o místních datech naleznete v tématu [přístup k místním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Viz také

- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Publikování řešení pro Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Postupy: publikování řešení pro systém Office pomocí technologie ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Postupy: instalace řešení ClickOnce pro sadu Office](/previous-versions/bb608592(v=vs.110))
- [Postupy: publikování řešení Office na úrovni dokumentu na server SharePoint pomocí technologie ClickOnce](/previous-versions/bb608595(v=vs.110))
- [Vytvoření vlastního instalačního programu pro řešení ClickOnce pro Office](/previous-versions/bb772078(v=vs.110))