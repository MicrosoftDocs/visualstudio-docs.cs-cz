---
title: 'Postupy: publikování aplikace WPF s povolenými vizuálními styly | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3691f782f317667b56f6bf3641c0f4c6a703eda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697576"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Postupy: Publikování aplikace WPF s povolenými vizuálními styly

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizuální styly umožňují změnu vzhledu běžných ovládacích prvků na základě motivu zvoleného uživatelem. Ve výchozím nastavení nejsou povoleny vizuální styly pro aplikace Windows Presentation Foundation (WPF), takže je musíte povolit ručně. Nicméně povolení vizuálních stylů pro aplikaci WPF a následné publikování řešení způsobí chybu. Toto téma popisuje, jak vyřešit tuto chybu a proces pro publikování aplikace WPF s povolenými vizuálními styly. Další informace o vizuálních stylech naleznete v tématu [Přehled vizuálních stylů](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Další informace o chybové zprávě najdete v tématu [řešení konkrétních chyb v nasazeních ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Chcete-li vyřešit chybu a publikovat řešení, je nutné provést následující úlohy:

- [Publikování řešení bez povolených vizuálních stylů](#BKMK_publishsolwovs).

- [Vytvořte soubor manifestu](#BKMK_CreateManifest).

- [Vložte soubor manifestu do spustitelného souboru publikovaného řešení](#BKMK_embedmanifest).

- [Podepište manifesty aplikace a nasazení](#BKMK_signappdeplyman).

  Pak můžete publikované soubory přesunout do umístění, ze kterého mají koncoví uživatelé instalovat aplikaci.

## <a name="publish-the-solution-without-visual-styles-enabled"></a><a name="BKMK_publishsolwovs"></a> Publikování řešení bez povolených vizuálních stylů

1. Ujistěte se, že váš projekt nemá povoleny vizuální styly. Nejprve v souboru manifestu projektu vyhledejte následující kód XML. Pokud je kód XML přítomen, vložte jej do kódu XML značkou komentáře.

     Ve výchozím nastavení nejsou vizuální styly povoleny.

    ```xml
    <dependency>
        <dependentAssembly>
          <assemblyIdentity
              type="win32"
              name="Microsoft.Windows.Common-Controls"
              version="6.0.0.0"
              processorArchitecture="*"
              publicKeyToken="6595b64144ccf1df"
              language="*" />
        </dependentAssembly>
      </dependency>
    ```

     Následující postupy ukazují, jak otevřít soubor manifestu přidružený k vašemu projektu.

    **Otevření souboru manifestu v Visual Basic projektu**

    1. V panelu nabídek vyberte položku **projekt**, vlastnosti _ProjectName_**Properties**, kde *ProjectName* je název vašeho projektu WPF.

         Zobrazí se stránky vlastností projektu WPF.

    2. Na kartě **aplikace** vyberte možnost **Zobrazit nastavení systému Windows**.

         Otevře se soubor App. manifest v **editoru kódu**.

    **Otevření souboru manifestu v projektu C#**

    1. V panelu nabídek vyberte položku **projekt**, vlastnosti _ProjectName_**Properties**, kde *ProjectName* je název vašeho projektu WPF.

         Zobrazí se stránky vlastností projektu WPF.

    2. Na kartě **aplikace** si poznamenejte název, který se zobrazí v poli manifest. Toto je název manifestu, který je přidružen k vašemu projektu.

        > [!NOTE]
        > Pokud se v poli manifest objeví **manifest s výchozím nastavením** nebo se **vytvoří aplikace bez manifestu** , vizuální styly nejsou povolené. Pokud se název souboru manifestu zobrazí v poli manifest, přejděte k dalšímu kroku tohoto postupu.

    3. V **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory** ().

         Toto tlačítko zobrazuje všechny položky projektu, včetně těch, které byly vyloučeny, a těch, které jsou normálně skryté. Soubor manifestu se zobrazí jako položka projektu.

2. Sestavte a publikujte své řešení. Další informace o tom, jak publikovat řešení, naleznete v tématu [How to: Publish a ClickOnce aplikace using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a><a name="BKMK_CreateManifest"></a> Vytvořit soubor manifestu

1. Vložte následující kód XML do souboru poznámkového bloku.

     Tento kód XML popisuje sestavení, které obsahuje ovládací prvky, které podporují vizuální styly.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
     <asmv1:assembly manifestVersion="1.0"
         xmlns="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <dependency>
        <dependentAssembly>
          <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="*"
            publicKeyToken="6595b64144ccf1df"
            language="*" />
        </dependentAssembly>
      </dependency>
    </asmv1:assembly>
    ```

2. V programu Poznámkový blok klikněte na **soubor**a pak klikněte na **Uložit jako**.

3. V dialogovém okně **Uložit jako** v rozevíracím seznamu **Uložit jako typ** vyberte možnost **všechny soubory**.

4. Do pole **název souboru** zadejte název souboru a na konec názvu souboru přidejte **. manifest** . Například: **Themes. manifest**.

5. Zvolte tlačítko **Procházet složky** , vyberte libovolnou složku a pak klikněte na **Uložit**.

    > [!NOTE]
    > Zbývající postupy předpokládají, že název tohoto souboru je **Themes. manifest** a že je soubor uložen do adresáře C:\Temp ve vašem počítači.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a><a name="BKMK_embedmanifest"></a> Vložte soubor manifestu do spustitelného souboru publikovaného řešení.

1. Otevřete **příkazový řádek sady Visual Studio**.

    Další informace o tom, jak otevřít **příkazový řádek sady Visual Studio**, najdete v tématu [výzvy k zadání příkazu](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219).

   > [!NOTE]
   > Zbývající kroky vedou k řešení následující předpoklady:
   >
   > - Název řešení je **MyWPFProject**.
   > - Řešení je umístěno v následujícím adresáři: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - Řešení je Publikováno v následujícím adresáři: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - Nejnovější verze publikovaných souborů aplikace se nachází v následujícím adresáři: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Nemusíte používat název nebo umístění adresářů popsané výše. Název a umístění popsané výše se používají pouze k ilustraci kroků požadovaných k publikování vašeho řešení.

2. Na příkazovém řádku změňte cestu k adresáři, který obsahuje nejaktuálnější verzi publikovaných souborů aplikace. Následující příklad demonstruje tento krok.

   ```
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Na příkazovém řádku spusťte následující příkaz pro vložení souboru manifestu do spustitelného souboru aplikace.

   ```
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a><a name="BKMK_signappdeplyman"></a> Podepsání manifestů aplikace a nasazení

1. Na příkazovém řádku spusťte následující příkaz, který odebere `.deploy` rozšíření ze spustitelného souboru v aktuálním adresáři.

   ```
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > V tomto příkladu se předpokládá, že Přípona souboru má jenom jeden soubor `.deploy` . Ujistěte se, že přejmenujete všechny soubory v tomto adresáři, které mají `.deploy` příponu souboru.

2. Na příkazovém řádku spusťte následující příkaz pro podepsání manifestu aplikace.

   ```
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > V tomto příkladu se předpokládá, že podepisujete manifest pomocí `.pfx` souboru projektu. Pokud nepodepisujete manifest, můžete vynechat `–cf` parametr, který je použit v tomto příkladu. Pokud podepisujete manifest s certifikátem, který vyžaduje heslo, zadejte `–password` možnost ( `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` ).

3. Na příkazovém řádku spusťte následující příkaz, který přidá `.deploy` rozšíření k názvu souboru, který jste přejmenovali v předchozím kroku tohoto postupu.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > V tomto příkladu se předpokládá, že má `.deploy` Přípona souboru jenom jeden soubor. Ujistěte se, že jste přejmenovali všechny soubory v tomto adresáři, které dříve obsahovaly `.deploy` příponu názvu souboru.

4. Na příkazovém řádku spusťte následující příkaz pro podepsání manifestu nasazení.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > V tomto příkladu se předpokládá, že podepisujete manifest pomocí `.pfx` souboru projektu. Pokud nepodepisujete manifest, můžete vynechat `–cf` parametr, který je použit v tomto příkladu. Pokud podepisujete manifest s certifikátem, který vyžaduje heslo, zadejte `–password` možnost, jako v tomto příkladu: `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` .

   Po provedení těchto kroků můžete publikované soubory přesunout do umístění, ze kterého mají koncoví uživatelé instalovat aplikaci. Pokud máte v úmyslu řešení často aktualizovat, můžete tyto příkazy přesunout do skriptu a spustit skript pokaždé, když publikujete novou verzi.

## <a name="see-also"></a>Viz také

[Řešení konkrétních chyb v nasazeních ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md) 
 Přehled vizuálních [stylů](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e) 
 [Výzvy příkazového řádku](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)
