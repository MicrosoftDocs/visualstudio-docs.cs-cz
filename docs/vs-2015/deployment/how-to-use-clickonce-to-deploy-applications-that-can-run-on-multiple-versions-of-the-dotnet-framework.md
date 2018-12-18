---
title: 'Postupy: použití ClickOnce k nasazení aplikací, které můžou běžet na více verzích rozhraní .NET Framework | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 7731526b09ab3014b9f3256ee1f4e4d0dd653a34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259054"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Postupy: Použití ClickOnce k nasazení aplikací, jež lze provozovat na více verzích rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nasadit aplikaci, která se zaměřuje na více verzí rozhraní .NET Framework pomocí nasazení technologie ClickOnce. To vyžaduje generovat a aktualizujte manifesty aplikace a nasazení.  
  
> [!NOTE]
>  Před změnou aplikace pro cílení na více verzí rozhraní .NET Framework, měli byste zajistit, že vaše aplikace spuštěná ve více verzích rozhraní .NET Framework. Modul common language runtime verze se liší mezi [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] oproti .NET Framework 2.0, .NET Framework 3.0 a rozhraní .NET Framework 3.5.  
  
 Tento postup vyžaduje následující kroky:  
  
1.  Generovat manifesty aplikace a nasazení.  
  
2.  Změna manifestu nasazení, aby obsahoval více verzí rozhraní .NET Framework.  
  
3.  Změňte soubor app.config seznam kompatibilní verze modulu runtime rozhraní .NET Framework.  
  
4.  Změňte manifest aplikace k označení závislé sestavení jako sestavení rozhraní .NET Framework.  
  
5.  Podepište manifest aplikace.  
  
6.  Aktualizace a podepsání manifestu nasazení.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Pro generování manifestů aplikace a nasazení  
  
-   Publikování aplikace a vytvářet aplikace a soubory manifestu nasazení pomocí Průvodce publikováním nebo publikovat stránku Návrháře projektu. Další informace najdete v tématu [postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) nebo [publikovat stránku, Návrhář projektu](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Chcete-li změnit manifestu nasazení, aby obsahoval více verzí rozhraní .NET Framework  
  
1.  V adresáři pro publikování otevřete pomocí editoru XML v sadě Visual Studio manifest nasazení. Manifest nasazení má příponu .application.  
  
2.  Nahraďte kód XML mezi `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` a `</compatibleFrameworks>` elementy XML, který obsahuje seznam podporovaných verzí rozhraní .NET Framework pro vaši aplikaci.  
  
     V následující tabulce jsou uvedeny některé z dostupných verzí rozhraní .NET Framework a odpovídající kód XML, který můžete přidat do manifestu nasazení.  
  
    |Verze rozhraní .NET Framework|XML|  
    |----------------------------|---------|  
    |4 klienta|\<Framework targetVersion = "4.0" profile = supportedRuntime "Client" = "4.0.30319" / >|  
    |4 full|\<Framework targetVersion = "4.0" profile = "Úplné" supportedRuntime = "4.0.30319" / >|  
    |3.5 klienta|\<Framework targetVersion = "3.5" profile = supportedRuntime "Client" = "2.0.50727" / >|  
    |3.5 úplné|\<Framework targetVersion = "3.5" profile = "Úplné" supportedRuntime = "2.0.50727" / >|  
    |3.0|\<Framework targetVersion = "3.0" supportedRuntime = "2.0.50727" / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Chcete-li změnit soubor app.config seznam kompatibilní verze modulu runtime rozhraní .NET Framework  
  
1.  V Průzkumníku řešení otevřete soubor App.config pomocí editoru jazyka XML v sadě Visual Studio.  
  
2.  Nahradit (nebo přidat) kód XML mezi `<startup>` a `</startup>` elementy XML, který uvádí podporované moduly runtime rozhraní .NET Framework pro vaši aplikaci.  
  
     V následující tabulce jsou uvedeny některé z dostupných verzí rozhraní .NET Framework a odpovídající kód XML, který můžete přidat do manifestu nasazení.  
  
    |Verze modulu runtime rozhraní .NET framework|XML|  
    |------------------------------------|---------|  
    |4 klienta|\<supportedRuntime verze = sku "v4.0.30319" = ". NETFramework, verze = v4.0 profilu klienta = "/ >|  
    |4 full|\<supportedRuntime verze = sku "v4.0.30319" = ". NETFramework, verze = v4.0 "/ >|  
    |3.5 úplné|\<supportedRuntime version="v2.0.50727"/ >|  
    |3.5 klienta|\<supportedRuntime verze = sku "v2.0.50727" = "Client" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Chcete-li změnit manifestu aplikace k označení závislé sestavení jako sestavení rozhraní .NET Framework  
  
1.  V adresáři pro publikování otevřete manifest aplikace pomocí editoru jazyka XML v sadě Visual Studio. Manifest nasazení má příponu .manifest.  
  
2.  Přidat `group="framework"` na závislost XML pro sestavení sentinel (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, a `System.Data.Entity`). Například soubor XML by měl vypadat nějak takto:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Aktualizovat číslo verze `<assemblyIdentity>` – element pro Microsoft.Windows.CommonLanguageRuntime číslo verze pro rozhraní .NET Framework, který je nejmenším společným jmenovatelem. Například, pokud aplikace cílí na rozhraní .NET Framework 3.5 a [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)], použijte 2.0.50727.0 číslo verze a XML by měl vypadat nějak takto:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizace a opětovné podepisování aplikace a nasazení manifestů  
  
-   Aktualizace a opětovné podepisování manifestů aplikace a nasazení. Další informace najdete v tématu [postupy: opětovné podepsání aplikace a manifesty nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks > – Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<závislost > – Element](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce – Manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [Schéma konfiguračního souboru](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)



