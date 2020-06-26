---
title: 'Postupy: publikování aplikace WPF s povolenými vizuálními styly | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21c94cc7ab97070b138cbae108c617094faf09b5
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382208"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Postupy: publikování aplikace WPF s povolenými vizuálními styly

Vizuální styly umožňují změnu vzhledu běžných ovládacích prvků na základě motivu zvoleného uživatelem. Ve výchozím nastavení nejsou povoleny vizuální styly pro aplikace Windows Presentation Foundation (WPF), takže je musíte povolit ručně. Nicméně povolení vizuálních stylů pro aplikaci WPF a následné publikování řešení způsobí chybu. Toto téma popisuje, jak vyřešit tuto chybu a proces pro publikování aplikace WPF s povolenými vizuálními styly. Další informace o vizuálních stylech naleznete v tématu [Přehled vizuálních stylů](/windows/desktop/Controls/visual-styles-overview). Další informace o chybové zprávě najdete v tématu [řešení konkrétních chyb v nasazeních ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Chcete-li vyřešit chybu a publikovat řešení, je nutné provést následující úlohy:

- [Publikování řešení bez povolených vizuálních stylů](#publish-the-solution-without-visual-styles-enabled).

- [Vytvořte soubor manifestu](#create-a-manifest-file).

- [Vložte soubor manifestu do spustitelného souboru publikovaného řešení](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).

- [Podepište manifesty aplikace a nasazení](#sign-the-application-and-deployment-manifests).

  Pak můžete publikované soubory přesunout do umístění, ze kterého mají koncoví uživatelé instalovat aplikaci.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>Publikování řešení bez povolených vizuálních stylů

1. Ujistěte se, že váš projekt nemá povoleny vizuální styly. Nejprve v souboru manifestu projektu vyhledejte následující kód XML. Pokud je kód XML přítomen, vložte jej do kódu XML značkou komentáře.

     Ve výchozím nastavení nejsou vizuální styly povoleny.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     Následující postupy ukazují, jak otevřít soubor manifestu přidružený k vašemu projektu.

    **Otevření souboru manifestu v Visual Basic projektu**

    1. V panelu nabídek vyberte položku **projekt**, vlastnosti *ProjectName* **Properties**, kde *ProjectName* je název vašeho projektu WPF.

         Zobrazí se stránky vlastností projektu WPF.

    2. Na kartě **aplikace** vyberte možnost **Zobrazit nastavení systému Windows**.

         Otevře se soubor App. manifest v **editoru kódu**.

    **Otevření souboru manifestu v projektu C#**

    1. V panelu nabídek vyberte položku **projekt**, vlastnosti *ProjectName* **Properties**, kde *ProjectName* je název vašeho projektu WPF.

         Zobrazí se stránky vlastností projektu WPF.

    2. Na kartě **aplikace** si poznamenejte název, který se zobrazí v poli manifest. Toto je název manifestu, který je přidružen k vašemu projektu.

        > [!NOTE]
        > Pokud se v poli manifest objeví **manifest s výchozím nastavením** nebo se **vytvoří aplikace bez manifestu** , vizuální styly nejsou povolené. Pokud se název souboru manifestu zobrazí v poli manifest, přejděte k dalšímu kroku tohoto postupu.

    3. V **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory**.

         Toto tlačítko zobrazuje všechny položky projektu, včetně těch, které byly vyloučeny, a těch, které jsou normálně skryté. Soubor manifestu se zobrazí jako položka projektu.

2. Sestavte a publikujte své řešení. Další informace o tom, jak publikovat řešení, naleznete v tématu [How to: Publish a ClickOnce aplikace using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a>Vytvořit soubor manifestu

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
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. V programu Poznámkový blok klikněte na **soubor**a pak klikněte na **Uložit jako**.

3. V dialogovém okně **Uložit jako** v rozevíracím seznamu **Uložit jako typ** vyberte možnost **všechny soubory**.

4. Do pole **název souboru** zadejte název souboru a na konec názvu souboru přidejte *. manifest* . Například: *Themes. manifest*.

5. Zvolte tlačítko **Procházet složky** , vyberte libovolnou složku a pak klikněte na **Uložit**.

    > [!NOTE]
    > Zbývající postupy předpokládají, že název tohoto souboru je *Themes. manifest* a že je soubor uložen do adresáře *C:\Temp* ve vašem počítači.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Vložte soubor manifestu do spustitelného souboru publikovaného řešení.

1. Otevřete **příkazový řádek sady Visual Studio**.

    Další informace o tom, jak otevřít **příkazový řádek sady Visual Studio**, najdete v tématu [výzvy k zadání příkazu](/dotnet/framework/tools/developer-command-prompt-for-vs).

   > [!NOTE]
   > Zbývající kroky vedou k řešení následující předpoklady:
   >
   > - Název řešení je **MyWPFProject**.
   > - Řešení je umístěno v následujícím adresáři: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - Řešení je Publikováno v následujícím adresáři: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - Nejnovější verze publikovaných souborů aplikace se nachází v následujícím adresáři:`%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Nemusíte používat název nebo umístění adresářů popsané výše. Název a umístění popsané výše se používají pouze k ilustraci kroků požadovaných k publikování vašeho řešení.

2. Na příkazovém řádku změňte cestu k adresáři, který obsahuje nejaktuálnější verzi publikovaných souborů aplikace. Následující příklad demonstruje tento krok.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Na příkazovém řádku spusťte následující příkaz pro vložení souboru manifestu do spustitelného souboru aplikace.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>Podepsání manifestů aplikace a nasazení

1. Na příkazovém řádku spusťte následující příkaz, který odebere rozšíření *. deploy* ze spustitelného souboru v aktuálním adresáři.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > V tomto příkladu se předpokládá, že má Přípona souboru *. deploy* pouze jeden soubor. Ujistěte se, že přejmenujete všechny soubory v tomto adresáři, které mají příponu souboru *. deploy* .

2. Na příkazovém řádku spusťte následující příkaz pro podepsání manifestu aplikace.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > V tomto příkladu se předpokládá, že podepisujete manifest pomocí souboru *. pfx* projektu. Pokud nepodepisujete manifest, můžete vynechat `-cf` parametr, který je použit v tomto příkladu. Pokud podepisujete manifest s certifikátem, který vyžaduje heslo, zadejte `-password` možnost ( `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` ).

3. Na příkazovém řádku spusťte následující příkaz, který přidá rozšíření *. deploy* do názvu souboru, který jste přejmenovali v předchozím kroku tohoto postupu.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > Tento příklad předpokládá, že pouze jeden soubor měl příponu souboru *. deploy* . Ujistěte se, že přejmenujete všechny soubory v tomto adresáři, které dříve obsahovaly příponu názvu souboru *. deploy* .

4. Na příkazovém řádku spusťte následující příkaz pro podepsání manifestu nasazení.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > V tomto příkladu se předpokládá, že podepisujete manifest pomocí souboru *. pfx* projektu. Pokud nepodepisujete manifest, můžete vynechat `-cf` parametr, který je použit v tomto příkladu. Pokud podepisujete manifest s certifikátem, který vyžaduje heslo, zadejte `-password` možnost, jako v tomto příkladu: `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

   Po provedení těchto kroků můžete publikované soubory přesunout do umístění, ze kterého mají koncoví uživatelé instalovat aplikaci. Pokud máte v úmyslu řešení často aktualizovat, můžete tyto příkazy přesunout do skriptu a spustit skript pokaždé, když publikujete novou verzi.

## <a name="see-also"></a>Viz také

-[Řešení konkrétních chyb v nasazeních ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Přehled vizuálních stylů](/windows/desktop/Controls/visual-styles-overview)
- [Povolení vizuálních stylů](/windows/desktop/Controls/cookbook-overview)
- [Výzvy příkazového řádku](/dotnet/framework/tools/developer-command-prompt-for-vs)
