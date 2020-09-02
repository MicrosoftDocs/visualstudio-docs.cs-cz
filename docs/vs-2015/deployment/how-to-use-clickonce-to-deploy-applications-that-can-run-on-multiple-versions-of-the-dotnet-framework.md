---
title: 'Postupy: použití ClickOnce k nasazení aplikací, které lze spustit na více verzích .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 164fe64f360e41c06ef3f7bfd2d8091a6ebefecd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679937"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Postupy: Použití ClickOnce k nasazení aplikací, jež lze provozovat na více verzích rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nasadit aplikaci, která se zaměřuje na více verzí .NET Framework pomocí technologie nasazení ClickOnce. To vyžaduje, abyste vygenerovali a aktualizovali manifesty aplikace a nasazení.  
  
> [!NOTE]
> Před změnou aplikace tak, aby byla cílena na více verzí .NET Framework, je nutné zajistit, aby aplikace běžela s více verzemi .NET Framework. Verze modulu CLR (Common Language Runtime) je odlišná mezi [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] .NET Framework 2,0, .NET Framework 3,0 a .NET Framework 3,5.  
  
 Tento proces vyžaduje následující kroky:  
  
1. Vygenerujte manifesty aplikace a nasazení.  
  
2. Změňte manifest nasazení tak, aby vypisovat více .NET Framework verzí.  
  
3. Změňte soubor app.config tak, aby vypisovat kompatibilní verze .NET Framework runtime.  
  
4. Změňte manifest aplikace tak, aby označil závislé sestavení jako sestavení .NET Framework.  
  
5. Podepište manifest aplikace.  
  
6. Aktualizujte a podepište manifest nasazení.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Generování manifestů aplikace a nasazení  
  
- Použijte Průvodce publikováním nebo stránku publikovat Návrháře projektu k publikování aplikace a generování souborů manifestu aplikace a nasazení. Další informace naleznete v tématu [How to: Publish a Project using](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) -Publish Wizard or Publishing [Page Designer](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Změna manifestu nasazení na výpis více verzí .NET Framework  
  
1. V adresáři Publisher otevřete manifest nasazení pomocí editoru XML v aplikaci Visual Studio. Manifest nasazení má příponu názvu souboru. Application.  
  
2. Nahraďte kód XML mezi `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` elementy a kódem `</compatibleFrameworks>` XML, který uvádí podporované verze .NET Framework pro vaši aplikaci.  
  
     V následující tabulce jsou uvedeny některé dostupné verze .NET Framework a odpovídající kód XML, který můžete přidat do manifestu nasazení.  
  
    |Verze rozhraní .NET Framework|XML|  
    |----------------------------|---------|  
    |4 klienti|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|  
    |4 úplné|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|  
    |klient 3,5|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|  
    |3,5 úplné|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|  
    |3,0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Změna souboru app.config tak, aby vypisovat kompatibilní verze .NET Framework runtime  
  
1. V Průzkumník řešení otevřete App.config souboru pomocí editoru XML v aplikaci Visual Studio.  
  
2. Nahraďte (nebo přidejte) kód XML mezi `<startup>` elementy a kódem `</startup>` XML, který obsahuje seznam podporovaných .NET Framework runtime pro vaši aplikaci.  
  
     V následující tabulce jsou uvedeny některé dostupné verze .NET Framework a odpovídající kód XML, který můžete přidat do manifestu nasazení.  
  
    |Verze modulu runtime .NET Framework|XML|  
    |------------------------------------|---------|  
    |4 klienti|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|  
    |4 úplné|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|  
    |3,5 úplné|\<supportedRuntime version="v2.0.50727"/>|  
    |klient 3,5|\<supportedRuntime version="v2.0.50727" sku="Client"/>|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Změna manifestu aplikace tak, aby označila závislá sestavení jako .NET Framework sestavení  
  
1. V adresáři Publisher otevřete manifest aplikace pomocí editoru XML v aplikaci Visual Studio. Manifest nasazení má příponu názvu souboru. manifest.  
  
2. Přidejte `group="framework"` do závislosti XML pro sestavení Sentinel (,, `System.Core` `WindowsBase` `Sentinel.v3.5Client` a `System.Data.Entity` ). Například XML by mělo vypadat takto:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3. Aktualizujte číslo verze `<assemblyIdentity>` elementu Microsoft. Windows. CommonLanguageRuntime na číslo verze .NET Framework, které je nejnižším společným jmenovatelem. Například pokud je aplikace cílena .NET Framework 3,5 a [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , použijte číslo verze 2.0.50727.0 a XML by mělo vypadat takto:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizace a opětovné podepsání manifestů aplikace a nasazení  
  
- Aktualizujte a znovu podepište manifesty aplikace a nasazení. Další informace najdete v tématu [Postup: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks> Objekt](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependency> Objekt](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)   
 [Schéma konfiguračního souboru](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)
