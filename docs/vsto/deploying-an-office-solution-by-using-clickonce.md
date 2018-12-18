---
title: Nasazení řešení Office s použitím technologie ClickOnce
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e46a0bdc23ee16c4821d3da751d5a90aa62a14c3
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673065"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Nasazení řešení Office s použitím technologie ClickOnce
  Vaše řešení pro Office v méně kroků můžete nasadit, když použijete ClickOnce. Když publikujete aktualizace, vaše řešení je automaticky rozpozná a nainstaluje. Technologie ClickOnce ale vyžaduje, aby bylo řešení nainstalováno zvlášť pro každého uživatele počítače. Proto byste měli zvážit použití Instalační služby systému Windows (*MSI*) je-li více než jeden uživatel vaše řešení bude používat ve stejném počítači.  

## <a name="in-this-topic"></a>V tomto tématu  

- [Publikování řešení](#Publish)  

- [Rozhodnutí o způsobu zajištění důvěryhodnosti řešení](#Trust)  

- [Pomoc uživatelům s instalací řešení](#Helping)  

- [Umístění dokumentu řešení do počítače koncového uživatele (pouze přizpůsobení na úrovni dokumentu)](#Put)  

- [Umístění dokumentu řešení na server, na kterém běží SharePoint (pouze přizpůsobení na úrovni dokumentu)](#SharePoint)  

- [Vytvoření vlastního instalačního programu](#Custom)  

- [Publikování aktualizace](#Update)  

- [Změna umístění instalace řešení](#Location)  

- [Vrácení řešení zpět na předchozí verzi](#Roll)  

  Další informace o tom, jak nasadit řešení pro Office vytvořením souboru Instalační služby systému Windows najdete v tématu [nasazení řešení Office s použitím Instalační služby systému Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  

##  <a name="Publish"></a> Publikování řešení  
 Řešení můžete publikovat pomocí **Průvodce publikováním** nebo **Návrháře projektu**. V tomto postupu budete používat **Návrháře projektu** protože poskytuje kompletní sadu možnosti publikování. Zobrazit [Průvodci publikováním &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  

#### <a name="to-publish-the-solution"></a>Publikování řešení  

1. V **Průzkumníka řešení**, klikněte na uzel s názvem projektu.  

2. V panelu nabídky zvolte **projektu**, *ProjectName* **vlastnosti**.  

3. V **Návrháře projektu**, zvolte **publikovat** kartu, která ukazuje následující obrázek.  

    ![Na kartě Publikovat v Návrháři projektu](../vsto/media/vsto-publishtab.png "kartě Publikovat v Návrháři projektu")  

4. V **umístění složky pro publikování (ftp server nebo cesta k souboru)** zadejte cestu ke složce, kam chcete **Návrháře projektu** zkopírovat soubory řešení.  

    Můžete zadat některý z následujících typů cest.  

   -   Místní cesta (například *C:\FolderName\FolderName*).  

   -   Cestu (Uniform Naming Convention) do složky v síti (například  *\\\ServerName\FolderName*).  

   -   Relativní cesta (například *PublishFolder\\*, což je složka, ve kterém je projekt publikován ve výchozím nastavení).  

5. V **adresa URL složky instalace** pole, zadejte plně kvalifikovanou cestu k umístění, ve kterém řešení najdou koncoví uživatelé.  

    Pokud umístění ještě neznáte, nemusíte zadávat nic do tohoto pole. Ve výchozím nastavení hledá technologie ClickOnce aktualizace ve složce, ze které uživatelé řešení instalují.  

6. Zvolte **požadavky** tlačítko.  

7. V **požadavky** dialogového okna zkontrolujte, zda **vytvořit instalační program pro nainstalování nezbytných součástí** je zaškrtnuto políčko.  

8. V **vyberte předpoklady k instalaci** vyberte zaškrtávací políčka **Windows Installer 4.5** a odpovídající balíček rozhraní .NET Framework.  

    Například pokud vaše řešení cílí [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zaškrtněte políčka pro **Windows Installer 4.5** a **Microsoft .NET Framework 4.5 Full**.  

9. Pokud vaše řešení cílí na rozhraní .NET Framework 4.5, také vybrat **Visual Studio 2010 Tools for Office Runtime** zaškrtávací políčko.  

    > [!NOTE]  
    >  Ve výchozím nastavení toto zaškrtávací políčko nezobrazuje. Aby se toto zaškrtávací políčko zobrazilo, je nutné vytvořit balíček zaváděcího nástroje. Zobrazit [vytvoření balíčku zaváděcího nástroje pro Office 2013 VSTO doplněk pomocí Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).  

10. V části **Zadejte prosím umístění pro nainstalování součástí**, zvolte jednu z možností, které se zobrazí a klikněte na tlačítko **OK** tlačítko.  

     Jednotlivé možnosti jsou popsány v následující tabulce.  

    |Možnost|Popis|  
    |------------|-----------------|  
    |**Stáhnout nezbytné součásti z webu dodavatele součástí**|Uživatel bude vyzván, aby od dodavatele stáhl a nainstaloval nezbytné součásti.|  
    |**Stáhnout součásti ze stejného umístění, jako je má aplikace**|Požadovaný software bude nainstalován spolu s řešením. Pokud zvolíte tuto možnost, sada Visual Studio za vás zkopíruje všechny požadované balíčky do umístění pro publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|  
    |**Stáhnout nezbytné součásti z následujícího umístění**|Sada Visual Studio zkopíruje všechny balíčky požadovaných součástí do zadaného umístění a nainstaluje je společně s řešením.|  

     Zobrazit [dialogové okno požadavky](/visualstudio/ide/reference/prerequisites-dialog-box).  

11. Zvolte **aktualizace** tlačítko, určete, jak často chcete každý koncový uživatel doplňku VSTO nebo vlastní nastavení pro kontrolu aktualizací a klikněte na tlačítko **OK** tlačítko.  

    > [!NOTE]  
    >  Pokud nasazení provádíte pomocí disku CD-ROM nebo vyměnitelné jednotky, zvolte **nikdy Nezjišťovat dostupnost aktualizací** přepínač.  

     Informace o tom, jak publikovat aktualizace najdete v tématu [publikování aktualizace](#Update).  

12. Zvolte **možnosti** tlačítko, prohlédněte si možnosti v **možnosti** dialogové okno a potom vyberte **OK** tlačítko.  

13. Zvolte **publikovat** tlačítko.  

     Sada Visual Studio přidá následující složky a soubory do složky pro publikování, kterou jste zadali v předchozím kroku tohoto postupu.  

    - **Soubory aplikace** složky.  

    - Instalační program  

    - Manifest nasazení, který odkazuje na manifest nasazení pro nejnovější verzi  

      **Soubory aplikace** složka obsahuje podsložky pro každou verzi, kterou publikujete. Jednotlivé podsložky pro konkrétní verzi obsahují následující soubory.  

    - Manifest aplikace  

    - Manifest nasazení  

    - Sestavení přizpůsobení  

      Následující ilustrace znázorňuje strukturu složky pro publikování pro doplňku VSTO pro Outlook.  

      ![Struktura složky publikování](../vsto/media/publishfolderstructure.png "publikovat struktura složek")  

    > [!NOTE]  
    >  Technologie ClickOnce přidá *.deploy* rozšíření sestavení tak, aby zabezpečená Instalace Internetové informační služby (IIS) soubory neblokovala kvůli nebezpečné příponě. Když uživatel nainstaluje řešení, technologie ClickOnce odebere *.deploy* rozšíření.  

14. Zkopírujte soubory řešení do umístění instalace, které jste zadali v předchozím kroku tohoto postupu.  

##  <a name="Trust"></a> Rozhodnutí o způsobu zajištění důvěryhodnosti řešení  
 Aby bylo možné řešení spustit v počítačích uživatelů, musíte buď zajistit jeho důvěryhodnost, nebo uživatelé musejí při instalaci řešení reagovat na výzvu k potvrzení jeho důvěryhodnosti. Pokud chcete zajistit důvěryhodnost řešení, podepište manifesty pomocí certifikátu, který určuje známého a důvěryhodného vydavatele. Zobrazit [důvěryhodnosti řešení pomocí podepsání manifestů aplikace a nasazení](../vsto/granting-trust-to-office-solutions.md#Signing).  

 Pokud nasazujete přizpůsobení úrovni dokumentu a chcete dokument umístit do složky v počítači uživatele nebo zpřístupnit dokument na webu služby SharePoint, ujistěte se, zda sada Office považuje umístění dokumentu. Zobrazit [udělit důvěryhodnost dokumenty](../vsto/granting-trust-to-documents.md).  

##  <a name="Helping"></a> Pomoc uživatelům s instalací řešení  
 Uživatelé mohou řešení nainstalovat tak, že spustí instalační program, otevřou manifest nasazení nebo, v případě přizpůsobení na úrovni dokumentu, přímo otevřou dokument. Osvědčeným postupem je instalace řešení pomocí instalačního programu. Ostatní dva přístupy nezajišťují, že je nainstalovaný požadovaný software. Pokud uživatelé chtějí otevřít dokument z umístění instalace, musejí jej přidat do seznamu důvěryhodných umístění v Centru zabezpečení aplikace Office.  

### <a name="opening-the-document-of-a-document-level-customization"></a>Otevření dokumentu přizpůsobení na úrovni dokumentu  
 Uživatelé mohou otevřít dokument přizpůsobení na úrovni dokumentu přímo z umístění instalace nebo tak, že dokument zkopírují do svého počítače a poté otevřou jeho místní kopii.  

 Osvědčeným postupem je, že by uživatelé měli otevřít kopii dokumentu ve svém počítači, aby nemohla nastat situace, kdy se více uživatelů současně pokusí otevřít stejnou kopii. Pro vynucení tohoto postupu můžete nakonfigurovat instalační program tak, aby dokument zkopíroval do počítačů uživatelů. Zobrazit [umístění dokumentu řešení do počítače koncového uživatele (pouze přizpůsobení na úrovni dokumentu)](#Put).  

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Instalace řešení pomocí otevření manifestu nasazení z webu služby IIS  
 Uživatelé mohou nainstalovat řešení pro Office tak, že z webu otevřou manifest nasazení. Zabezpečená Instalace Internetové informační služby (IIS) ale zablokuje soubory, které mají *.vsto* rozšíření. Typ MIME musí být definován ve službě IIS před nasazením řešení pro Office pomocí služby IIS.  

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Přidání typu MIME .vsto do služby IIS 6.0  

1.  Na serveru, na kterém běží služby IIS 6.0, zvolte **Start** > **všechny programy** > **nástroje pro správu**  >   **Internetové informační služby (IIS) správce**. 

2.  Zvolte název počítače, **weby** složku nebo webový server, který konfigurujete.  

3.  V panelu nabídky zvolte **akce** > **vlastnosti**.  

4.  Na **hlavičky protokolu HTTP** , vyberte **typy MIME** tlačítko.  

5.  V **typy MIME** okna, vyberte **nový** tlačítko.  

6.  V **typ MIME** okno, zadejte **.vsto** jako rozšíření, zadejte **application/x-ms-vsto** jako MIME typu a poté použijte nová nastavení.  

    > [!NOTE]  
    >  Aby se změny projevily, je nutné restartovat službu Publikování na webu nebo počkat na recyklaci pracovního procesu. Musíte pak vyprázdnit diskovou mezipaměť prohlížeče a poté se pokusí otevřít *.vsto* soubor znovu.  

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Chcete-li přidat typ MIME .vsto do služby IIS 7.0  

1.  Na serveru, na kterém běží služby IIS 7.0, zvolte **Start** > **všechny programy** > **Příslušenství**.  

2.  Otevřete místní nabídku pro **příkazového řádku**a klikněte na tlačítko **spustit jako správce.**  

3.  V **otevřít** zadejte následující cestu a klikněte na tlačítko **OK** tlačítko.  

    ```cmd
    %windir%\system32\inetsrv   
    ```  

4.  Zadejte následující příkaz a poté použijte nová nastavení.  

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  

    > [!NOTE]  
    >  Aby se změny projevily, je nutné restartovat službu Publikování na webu nebo počkat na recyklaci pracovního procesu. Musíte pak vyprázdnit diskovou mezipaměť prohlížeče a poté se pokusí otevřít *.vsto* soubor znovu.  

##  <a name="Put"></a> Umístění dokumentu řešení do počítače koncového uživatele (pouze přizpůsobení na úrovni dokumentu)  
 Můžete kopírovat dokument řešení do počítače koncového uživatele pro ně tak, že vytvoříte akci po nasazení. Tímto způsobem, uživatel nebude muset ručně kopírovat dokument z umístění instalace na svém počítači po instalaci vašeho řešení. Bude nutné vytvořit třídu, která definuje akci po nasazení, vytváření a publikování řešení, upravit manifest aplikace a znovu podepsat manifest aplikace a nasazení.  

 V následujících postupech se předpokládá, že je název vašeho projektu **ExcelWorkbook** a publikování řešení **C:\publish** adresáře v počítači.  

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Vytvoření třídy, která definuje akci po nasazení  

1. V panelu nabídky zvolte **souboru** > **přidat** > **nový projekt**.  

2. V **přidat nový projekt** v dialogu **nainstalované šablony** podokně zvolte **Windows** složky.  

3. V **šablony** podokně, vyberte **knihovny tříd** šablony.  

4. V **název** zadejte **FileCopyPDA**a klikněte na tlačítko **OK** tlačítko.  

5. V **Průzkumníka řešení**, zvolte **FileCopyPDA** projektu.  

6. V panelu nabídky zvolte **projektu** > **přidat odkaz**.  

7. Na **.NET** kartu, přidejte odkazy na `Microsoft.VisualStudio.Tools.Applications.Runtime` a `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.  

8. Přejmenujte třídu na `FileCopyPDA`a poté nahraďte obsah souboru s kódem. Tento kód provede následující:  

   - Zkopíruje dokument na plochu uživatele.  

   - Změní vlastnost _AssemblyLocation pomocí relativní cesty na plně kvalifikovanou cestu k manifestu nasazení.  

   - Odstraní soubor, pokud uživatel řešení odinstaluje.  

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  

### <a name="build-and-publish-the-solution"></a>Sestavení a publikování řešení  

1.  V **Průzkumníka řešení**, otevřete místní nabídku **FileCopyPDA** projektu a klikněte na tlačítko **sestavení**.  

2.  Otevřete místní nabídku **ExcelWorkbook** projektu a klikněte na tlačítko **sestavení**.  

3.  Otevřete místní nabídku **ExcelWorkbook** projektu a klikněte na tlačítko **přidat odkaz**.  

4.  V **přidat odkaz** dialogového okna zvolte **projekty** kartě **FileCopyPDA**a klikněte na tlačítko **OK** tlačítko.  

5.  V **Průzkumníka řešení**, zvolte **ExcelWorkbook** projektu.  

6.  V řádku nabídek zvolte **projektu** > **novou složku**.  

7.  Zadejte **Data**a klikněte na tlačítko **Enter** klíč.  

8.  V **Průzkumníka řešení**, zvolte **Data** složky.  

9. V panelu nabídky zvolte **projektu** > **přidat existující položku**.  

10. V **přidat existující položku** dialogové okno, přejděte do výstupní adresář **ExcelWorkbook** projektu, zvolte **ExcelWorkbook.xlsx** souboru a klikněte na tlačítko  **Přidat** tlačítko.  

11. V **Průzkumníka řešení** zvolte **ExcelWorkbook.xlsx** souboru.  

12. V **vlastnosti** okno Změnit **akce sestavení** vlastnost **obsahu** a **kopírovat do výstupního adresáře** vlastnost  **Kopírovat, pokud je novější**.  

     Po dokončení těchto kroků, svůj projekt bude vypadat podobně jako na následujícím obrázku.  

     ![Struktura projektu akci po nasazení. ](../vsto/media/vsto-postdeployment.png "Struktura akci po nasazení projektu.")  

13. Publikovat **ExcelWorkbook** projektu.  

### <a name="modify-the-application-manifest"></a>Úprava manifestu aplikace  

1.  Otevřít **c:\publish** adresáře pomocí **Průzkumníka souborů**.  

2.  Otevřete **soubory aplikace** složku a poté otevřete složku, která odpovídá nejnovější publikované verzi vašeho řešení.  

3.  Otevřít **ExcelWorkbook.dll.manifest** souboru v textovém editoru, jako je například Poznámkový blok.  

4.  Po `</vstav3:update>` prvku, přidejte následující kód. Pro atribut class `<vstav3:entryPoint>` elementu, použijte následující syntaxi: *NamespaceName.ClassName*. V následujícím příkladu název oboru názvů a třídy jsou stejné, takže je výsledný název vstupního bodu `FileCopyPDA.FileCopyPDA`.  

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

1.  V **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** složka, Kopírovat **ExcelWorkbook_TemporaryKey.pfx** soubor certifikátu a vložte ho do  *PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ složky.

2.  Otevřete příkazový řádek sady Visual Studio a potom změňte adresáře na **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ složky (například **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).  

3.  Podepište upravený manifest aplikace spuštěním následujícího příkazu:  

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  

     Zobrazí se zpráva „ExcelWorkbook.dll.manifest successfully signed“ („Soubor ExcelWorkbook.dll.manifest byl úspěšně podepsán.“).  

4.  Přejděte **c:\publish** složky a pak aktualizace a znaménko nasazení manifestu spuštěním následujícího příkazu:  

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  

    > [!NOTE]  
    >  V předchozím příkladu nahraďte část MostRecentVersionNumber číslo verze naposledy publikované verze vašeho řešení (například **1_0_0_4**).  

     Zobrazí se zpráva „ExcelWorkbook.vsto successfully signed“ („Soubor ExcelWorkbook.vsto byl úspěšně podepsán.“).  

5.  Kopírovat *ExcelWorkbook.vsto* do souboru **c:\publish\Application Files\ExcelWorkbook**\__část MostRecentVersionNumber_ adresáře.  

##  <a name="SharePoint"></a> Umístění dokumentu řešení na server, na kterém běží SharePoint (pouze přizpůsobení na úrovni dokumentu)  
 Přizpůsobení na úrovni dokumentu můžete pro koncové uživatele publikovat pomocí služby SharePoint. Když uživatelé přejdou na web služby SharePoint a dokument otevřou, modul runtime automaticky nainstaluje řešení ze sdílené síťové složky do místního počítače uživatele. Jakmile je řešení nainstalováno místně, bude přizpůsobení nadále fungovat i v případě, že je dokument zkopírován do jiného umístění, například na plochu.  

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Umístění dokumentu na server, na kterém je spuštěna služba SharePoint  

1.  Přidejte dokument řešení do knihovny dokumentů na webu služby SharePoint.  

2.  Proveďte jeden z následujících postupů:  

    -   Pomocí konfiguračního nástroje sady Office přidejte server, na němž je spuštěna služba SharePoint, do Centra zabezpečení v aplikaci Word nebo Excel na všech počítačích uživatelů.  

         Zobrazit [zásady zabezpečení a nastavení v aplikaci Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).  

    -   Postarejte se, aby každý uživatel provedl následující kroky.  

        1.  V místním počítači, spusťte aplikaci Word nebo Excel, zvolte **souboru** kartu a klikněte na tlačítko **možnosti** tlačítko.  

        2.  V **centrum** dialogového okna zvolte **důvěryhodná umístění** tlačítko.  

        3.  Vyberte **Povolit důvěryhodná umístění v síti (nedoporučuje se)** zaškrtněte políčko a klikněte na tlačítko **přidat nové umístění** tlačítko.  

        4.  V **cesta** zadejte adresu URL knihovny dokumentů služby SharePoint, která obsahuje dokument, který jste nahráli (například *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).  

             Nepřidávejte název výchozí webové stránky, jako například *default.aspx* nebo *AllItems.aspx*.  

        5.  Vyberte **podsložky tohoto umístění jsou také důvěryhodné** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  

             Když uživatelé otevřou dokument z webu služby SharePoint, dokument se otevře a nainstaluje se přizpůsobení. Uživatelé mohou dokument zkopírovat na svou plochu. Přizpůsobení bude stále možné spustit, protože vlastnosti v dokumentu odkazují na síťové umístění dokumentu.  

##  <a name="Custom"></a> Vytvoření vlastního instalačního programu  
 Můžete vytvořit vlastní instalační program pro vaše řešení pro Office, namísto použití instalačního programu, který je vytvořen při publikování řešení. Můžete například spustit instalaci pomocí přihlašovacího skriptu nebo můžete řešení nainstalovat pomocí dávkového souboru bez zásahu uživatele. Tyto scénáře fungují nejlépe, pokud jsou požadované součásti již nainstalovány v počítačích koncových uživatelů.  

 Jako součást procesu vlastní instalace volejte instalační nástroj pro řešení Office (*VSTOInstaller.exe*), který je ve výchozím nastavení nainstalován v následujícím umístění:  

 *%CommonProgramFiles%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*  

 Pokud nástroj není v dané oblasti, můžete použít **nenachází Runtime Setup\v4\InstallerPath** nebo **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4 \InstallerPath** najít cestu k tomuto klíči registru.  

 Můžete použít následující parametry s *VSTOinstaller.exe*.  


| Parametr | Definice |
|------------------| - |
| /Install nebo /I | Nainstaluje řešení. Za tímto parametrem musí následovat cesta k manifestu nasazení. Zadejte cestu v místním počítači, universal naming convention (UNC) sdílené složky. Můžete zadat místní cestu (*C:\FolderName\PublishFolder*), relativní cestu (*publikovat\\*), nebo plně kvalifikované umístění (*\\\ServerName\ Název složky* nebo http://<em>ServerName/FolderName</em>). |
| /Uninstall nebo /U | Odinstaluje řešení. Za tímto parametrem musí následovat cesta k manifestu nasazení. Můžete určit, že cesta může být na místním počítači, sdílené složky UNC. Můžete zadat místní cestu (*c:\FolderName\PublishFolder*), relativní cestu (*publikovat\\*), nebo plně kvalifikované umístění (*\\\ServerName\ Název složky* nebo http://<em>ServerName/FolderName</em>). |
| /Silent nebo /S | Při instalaci nebo odinstalaci se uživatelům nebudou zobrazovat výzvy k zadání vstupu ani žádné jiné zprávy. Pokud bude vyžadováno potvrzení důvěryhodnosti, přizpůsobení nejsou nainstalovány nebo aktualizovány. |
| /Help nebo /? | Zobrazí informace nápovědy. |

 Při spuštění *VSTOinstaller.exe*, může se zobrazit následující kódy chyb.  

|Kód chyby|Definice|  
|----------------|----------------|  
|0|Řešení bylo úspěšně nainstalováno či odinstalováno nebo se zobrazila nápověda nástroje VSTOInstaller.|  
|-100|Jeden nebo více parametrů příkazového řádku není platných nebo byly nastaveny více než jedenkrát. Další informace, zadejte "vstoinstaller /?" nebo se podívejte [vytvoření vlastního instalátoru pro řešení ClickOnce Office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|-101|Jeden nebo více parametrů příkazového řádku není platná. Pokud chcete získat další informace, zadejte příkaz "vstoinstaller /?".|  
|-200|Identifikátor URI manifestu nasazení není platná. Pokud chcete získat další informace, zadejte příkaz "vstoinstaller /?".|  
|-201|Řešení nelze nainstalovat, protože manifest nasazení není platná. Zobrazit [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).|  
|-202|Řešení nelze nainstalovat, protože Visual Studio Tools for Office části manifestu aplikace není platný. Zobrazit [manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).|  
|-203|Řešení nelze nainstalovat, protože došlo k chybě stahování. Zkontrolujte identifikátor URI nebo síťové umístění souboru manifestu nasazení a akci opakujte.|  
|-300|Řešení nelze nainstalovat, protože došlo k výjimce zabezpečení. Zobrazit [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).|  
|-400|Řešení nelze nainstalovat.|  
|-401|Řešení nelze odinstalovat.|  
|-500|Operace byla zrušena, protože řešení nelze nainstalovat nebo odinstalovat nebo nelze stáhnout manifest nasazení.|  

##  <a name="Update"></a> Publikování aktualizace  
 Pokud chcete aktualizovat řešení, můžete je znovu publikovat s použitím **Návrháře projektu** nebo **Průvodce publikováním**, a poté zkopírovat aktualizované řešení do umístění instalace. Při kopírování souborů do umístění instalace je nutné přepsat předchozí soubory.  

 Při příštím až řešení příště vyhledat aktualizace, bude najít a automaticky načte novou verzi.  

##  <a name="Location"></a> Změna umístění instalace řešení  
 Po publikování řešení můžete přidat nebo změnit cestu instalace. Změnit cestu instalace může být vhodné z některého z následujících důvodů:  

- Instalační program byl zkompilován ještě předtím, než byla známa cesta instalace.  

- Soubory řešení byly zkopírovány do jiného umístění.  

- Změnil se název nebo umístění serveru, který hostuje instalační soubory.  

  Pokud chcete pro řešení změnit cestu instalace, je nutné aktualizovat instalační program, který poté uživatelé musejí spustit. V případě přizpůsobení na úrovni dokumentu musejí uživatelé také aktualizovat vlastnost v dokumentu tak, aby odkazovala na nové umístění.  

> [!NOTE]  
>  Pokud nechcete žádat uživatele, aby aktualizovali vlastnosti dokumentu, které požádejte uživatele, aby získali aktualizovaný dokument z umístění instalace.  

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Změna cesty instalace v instalačním programu  

1. Otevřít **příkazového řádku** okna a poté přejděte do instalační složky.  

2. Spusťte instalační program a zahrnout `/url` parametr, který využívá novou cestou instalace jako řetězec.  

    Následující příklad ukazuje, jak změnit cestu instalace na umístění na webu společnosti Fabrikam. Tuto adresu URL můžete nahradit požadovanou cestou:  

   ```cmd  
   setup.exe /url="http://www.fabrikam.com/newlocation"  
   ```  

   > [!NOTE]  
   >  Pokud se zobrazí zpráva, že bude zrušena platnost podpisu spustitelného souboru, znamená to, že certifikát, pomocí něhož bylo řešení podepsáno, již není platný a vydavatel je neznámý. V důsledku toho budou uživatelé muset před instalací řešení potvrdit, že zdroj řešení považují za důvěryhodný.  

   > [!NOTE]  
   >  Chcete-li zobrazit aktuální hodnotu adresy URL, spusťte `setup.exe /url`.  

   Pro přizpůsobení na úrovni dokumentu musí uživatelé otevřít dokument a poté aktualizovat jeho vlastnosti _AssemblyLocation. To mohou uživatelé provést pomocí následujícího postupu.  

#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Aktualizace vlastnosti _AssemblyLocation v dokumentu  

1.  Na **souboru** kartě **informace**, které ukazuje následující obrázek.  

     ![Informace o kartě v aplikaci Excel](../vsto/media/vsto-infotab.png "kartě informace jsou v aplikaci Excel")  

2.  V **vlastnosti** klikněte na položku **Upřesnit vlastnosti**, které ukazuje následující obrázek.  

     ![Upřesňující vlastnosti v aplikaci Excel. ](../vsto/media/vsto-advanceddocumentproperties.png "Rozšířené vlastnosti v aplikaci Excel.")  

3.  Na **vlastní** kartu **vlastnosti** klikněte na položku _AssemblyLocation, jako je vidět na následujícím obrázku.  

     ![Vlastnost AssemblyLocation. ](../vsto/media/vsto-assemblylocationproperty.png "The AssemblyLocation vlastnost.")  

     **Hodnotu** pole obsahuje identifikátor manifestu nasazení.  

4.  Před identifikátor zadejte plně kvalifikovanou cestu souboru, za nímž následuje panelu ve formátu *cesta*|*identifikátor* (například *File://ServerName/ Název_složky/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.  

     Další informace o tom, jak formátovat tento identifikátor, naleznete v tématu [přehled vlastností dokumentu vlastní](../vsto/custom-document-properties-overview.md).  

5.  Zvolte **OK** tlačítko a pak uložte a zavřete dokument.  

6.  Nainstalujte řešení do zadaného umístění tak, že spustíte instalační program bez parametru /url.  

##  <a name="Roll"></a> Vrácení řešení zpět na předchozí verzi  
 Když vrátíte řešení zpět, budou uživatelé opět používat předchozí verzi tohoto řešení.  

#### <a name="to-roll-back-a-solution"></a>Vrácení řešení zpět  

1.  Otevřete umístění instalace řešení.  

2.  Na nejvyšší úrovni složky pro publikování, odstraňte manifest nasazení ( *.vsto* souboru).  

3.  Vyhledejte podsložku pro verzi, kterou chcete vrátit zpět.  

4.  Zkopírujte manifest nasazení z této podsložky do složky na nejvyšší úrovni.  

     Například, chcete-li vrátit zpět řešení, která je volána **OutlookAddIn1** z verze 1.0.0.1 na verzi 1.0.0.0, zkopírujte soubor **OutlookAddIn1.vsto** z **OutlookAddIn1_1_0_0_0** složky. Vložte soubor do na nejvyšší úrovni složky manifest nasazení specifické verze pro pro publikování **OutlookAddIn1_1_0_0_1** , který byl již existuje.  

     Následující ilustrace znázorňuje strukturu složky pro publikování v tomto příkladu.  

     ![Struktura složky publikování](../vsto/media/publishfolderstructure.png "publikovat struktura složek")  

     Až uživatel příště otevře aplikaci nebo upravený dokument, bude detekována změna manifestu nasazení. Předchozí verze řešení pro Office se spustí z mezipaměti technologie ClickOnce.  

> [!NOTE]  
>  Místní data jsou uložena pouze pro jednu předchozí verzi řešení. Pokud vrátíte zpět dvě verze, místní data zachována. Další informace o místních datech naleznete v tématu [přístup k lokálním a vzdáleným datům v aplikacích ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  

## <a name="see-also"></a>Viz také:  
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Publikování řešení pro systém Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Postupy: publikování řešení Office s použitím technologie ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Postupy: Instalace řešení ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)   
 [Postupy: publikování řešení Office úrovni dokumentu na SharePoint serveru s použitím technologie ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Vytvoření vlastního instalátoru pro řešení office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)  


