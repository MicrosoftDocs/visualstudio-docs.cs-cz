---
title: 'Postupy: publikování aplikace WPF s povolenými vizuálními styly | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: f03dc4ea85fe0f44ea2253da9544ace9b0068abc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922468"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Postupy: Publikování aplikace WPF s povolenými vizuálními styly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizuální styly povolit vzhled běžných ovládacích prvků do měnit v závislosti na motiv uživatelem. Ve výchozím nastavení nejsou povoleny vizuální styly pro aplikace Windows Presentation Foundation (WPF), takže je potřeba povolit ručně. Povolení vizuálních stylů pro aplikace WPF a pak tuto aplikaci publikovat řešení způsobí chybu. Toto téma popisuje, jak vyřešit tuto chybu a proces pro publikování aplikace WPF s povolenými vizuálními styly. Další informace o vizuálních stylů, najdete v části [vizuální styly přehled](http://msdn.microsoft.com/en-us/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Další informace o chybové zprávě naleznete v tématu [řešení konkrétních chyb v nasazeních ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Chcete-li vyřešit chybu a publikovat řešení, je třeba provést následující úkoly:  
  
- [Publikování řešení bez povolenými vizuálními styly](#BKMK_publishsolwovs).  
  
- [Vytvořit soubor manifestu](#BKMK_CreateManifest).  
  
- [Vložit soubor manifestu do spustitelného souboru publikované řešení](#BKMK_embedmanifest).  
  
- [Podepsání manifestů aplikace a nasazení](#BKMK_signappdeplyman).  
  
  Potom můžete přesunout publikované soubory do umístění, ze kterého chcete, aby koncoví uživatelé k instalaci aplikace.  
  
##  <a name="BKMK_publishsolwovs"></a> Publikování řešení bez povolenými vizuálními styly  
  
1.  Ujistěte se, že váš projekt nemá povolenými vizuálními styly. Nejprve zkontrolujte soubor manifestu projektu následující kód XML. Potom Pokud kód XML je k dispozici, uzavřete s značka komentáře XML.  
  
     Ve výchozím nastavení nejsou povoleny vizuální styly.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Následující postupy ukazují, jak otevřít soubor manifestu, který je přidružený k projektu.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Chcete-li otevřít soubor manifestu v projektu jazyka Visual Basic  
  
    1.  V panelu nabídky zvolte **projektu**, _ProjectName_**vlastnosti**, kde *ProjectName* je název vašeho projektu WPF.  
  
         Stránky vlastností pro váš projekt WPF se zobrazí.  
  
    2.  Na **aplikace** kartě **nastavení Windows zobrazení**.  
  
         Otevře se soubor app.manifest v **Editor kódu**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>Chcete-li otevřít soubor manifestu v projektu v jazyce C#  
  
    1.  V panelu nabídky zvolte **projektu**, _ProjectName_**vlastnosti**, kde *ProjectName* je název vašeho projektu WPF.  
  
         Stránky vlastností pro váš projekt WPF se zobrazí.  
  
    2.  Na **aplikace** kartu, poznamenejte si název, který se zobrazí v poli manifestu. Jde o název manifestu, který je přidružený k projektu.  
  
        > [!NOTE]
        >  Pokud **Vložit manifest s výchozím nastavením** nebo **vytvořit aplikaci bez manifestu** zobrazí v poli manifestu nejsou povoleny vizuální styly. Pokud název souboru manifestu se zobrazí v poli manifestu, pokračujte k dalšímu kroku v tomto postupu.  
  
    3.  V **Průzkumníka řešení**, zvolte **zobrazit všechny soubory** ().  
  
         Toto tlačítko zobrazí všechny položky projektu, včetně těch, které byly vyloučeny a ty, které jsou obvykle skryta. Soubor manifestu se zobrazí jako položku projektu.  
  
2.  Vytvářejte a publikujte vaše řešení. Další informace o tom, jak publikovat řešení, najdete v části [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Vytvořit soubor manifestu  
  
1.  Vložte následující kód XML do souboru poznámkového bloku.  
  
     Tato konfigurace XML popisuje sestavení, která obsahuje ovládací prvky, které podporují vizuální styly.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  V programu Poznámkový blok, klikněte na tlačítko **souboru**a potom klikněte na tlačítko **uložit jako**.  
  
3.  V **uložit jako** v dialogu **uložit jako typ** rozevíracího seznamu vyberte **všechny soubory**.  
  
4.  V **název_souboru** pole, zadejte název souboru a připojit **.manifest** na konec názvu souboru. Příklad: **themes.manifest**.  
  
5.  Zvolte **procházet složky** tlačítko, vyberte libovolnou složku a potom klikněte na tlačítko **Uložit**.  
  
    > [!NOTE]
    >  Zbývající postupech se předpokládá, že název tohoto souboru je **themes.manifest** a zda je soubor uložen do adresáře C:\temp počítače.  
  
##  <a name="BKMK_embedmanifest"></a> Vložit soubor manifestu do spustitelného souboru publikované řešení  
  
1. Otevřít **příkazový řádek sady Visual Studio**.  
  
    Další informace o tom, jak otevřít **příkazový řádek sady Visual Studio**, naleznete v tématu [příkazové řádky](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219).  
  
   > [!NOTE]
   >  Ve zbývajících krocích vytvořit následující předpoklady o řešení:  
   > 
   > - Název řešení je **MyWPFProject**.  
   >   -   Řešení se nachází v následujícím adresáři: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
   > 
   >   Publikování řešení na následující adresář: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
   >   -   Překopírujte nejnovější verzi souborů publikované aplikace se nachází v následujícím adresáři: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
   > 
   >   Není nutné použít název nebo umístění adresáře je popsáno výše. Název a umístění je popsáno výše se používají pouze pro ilustraci kroky potřebné k publikování vašich řešení.  
  
2. Na příkazovém řádku změňte cestu k adresáři, který obsahuje nejnovější verzi souborů publikované aplikace. Následující příklad ukazuje tento krok.  
  
   ```  
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
   ```  
  
3. Na příkazovém řádku spusťte následující příkaz, který vložit soubor manifestu do spustitelného souboru aplikace.  
  
   ```  
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
   ```  
  
##  <a name="BKMK_signappdeplyman"></a> Podepsání manifestů aplikace a nasazení  
  
1. Na příkazovém řádku spusťte následující příkaz k odebrání `.deploy` rozšíření ze spustitelného souboru v aktuálním adresáři.  
  
   ```  
   ren MyWPFApp.exe.deploy MyWPFApp.exe  
   ```  
  
   > [!NOTE]
   >  Tento příklad předpokládá, že má pouze jeden soubor `.deploy` příponu souboru. Ujistěte se, že je přejmenovat všechny soubory v tomto adresáři, které mají `.deploy` příponu souboru.  
  
2. Na příkazovém řádku spusťte následující příkaz k podepsání manifestu aplikace.  
  
   ```  
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  Tento příklad předpokládá podepsání manifestu pomocí `.pfx` souboru projektu. Pokud nejsou podepsání manifestu, můžete vynechat `–cf` parametr, který se používá v tomto příkladu. Pokud se přihlašujete manifest certifikátem, který vyžaduje heslo, zadejte `–password` možnost (`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`).  
  
3. Na příkazovém řádku spusťte následující příkaz pro přidání `.deploy` příponu názvu souboru, který jste přejmenovali v předchozím kroku tohoto postupu.  
  
   ```  
   ren MyWPFApp.exe MyWPFApp.exe.deploy  
   ```  
  
   > [!NOTE]
   >  Tento příklad předpokládá, že pouze jeden soubor měl `.deploy` příponu souboru. Ujistěte se, že je přejmenovat všechny soubory v tomto adresáři, které dříve měly `.deploy` příponu názvu souboru.  
  
4. Na příkazovém řádku spusťte následující příkaz k podepsání manifestu nasazení.  
  
   ```  
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  Tento příklad předpokládá podepsání manifestu pomocí `.pfx` souboru projektu. Pokud nejsou podepsání manifestu, můžete vynechat `–cf` parametr, který se používá v tomto příkladu. Pokud se přihlašujete manifest certifikátem, který vyžaduje heslo, zadejte `–password` možnosti, jako v následujícím příkladu:`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`.  
  
   Po provedení těchto kroků můžete přesunout publikované soubory do umístění, ze kterého chcete, aby koncoví uživatelé k instalaci aplikace. Pokud máte v úmyslu často aktualizovat řešení, můžete přesunout tyto příkazy do skriptu a spusťte skript pokaždé, když že publikujete novou verzi.  
  
## <a name="see-also"></a>Viz také  
 [Řešení konkrétních chyb v nasazeních ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Vizuální styly – přehled](http://msdn.microsoft.com/en-us/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Příkazové řádky](http://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)



