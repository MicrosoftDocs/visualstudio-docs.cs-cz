---
title: 'Postupy: určení adresu URL podpory pro jednotlivé předpoklady v nasazení ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e93e8ab84a751c447488e1b4dc6e3e6779b86b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913277"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Postupy: Zadejte adresu URL podpory pro jednotlivé předpoklady v nasazení ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] otestovat nasazení pro celou řadou požadavky, které musí být k dispozici v klientském počítači pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spuštění aplikace. Zahrnout požadovaná minimální verze těchto závislostí [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], verzi operačního systému a všechna sestavení, které musí být předinstalován v globální mezipaměti sestavení (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], však nemůže nainstalovat některý z těchto nezbytných podmínkách; Pokud není nalezen předpoklad, jednoduše zastaví instalaci a zobrazí dialogové okno s vysvětlením, proč se instalace nepovedla.  
  
 Existují dvě metody pro instalaci požadavků. Můžete nainstalovat pomocí aplikace zaváděcího nástroje. Alternativně můžete zadat adresu URL podpory pro jednotlivé předpoklady, které se zobrazí uživatelům na dialogové okno, pokud se nenajde kontrolu požadovaných součástí. Na stránce odkazuje tuto adresu URL může obsahovat odkazy na pokyny k instalaci požadované součásti. Pokud aplikace neuvádějí adresu URL podpory pro jednotlivé předpoklady [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zobrazí adresa URL podpory určená v manifestu nasazení pro aplikaci jako celek, pokud je definována.  
  
 Zatímco [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *Mage.exe*, a *MageUI.exe* všechny slouží ke generování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, žádný z těchto nástrojů přímo nepodporuje určení adresu URL podpory pro jednotlivce požadované součásti. Tento dokument popisuje postup upravení vašeho nasazení manifest aplikace a manifest nasazení pro zahrnutí těchto podporují adresy URL.  
  
### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Zadejte adresu URL podpory pro jednotlivé předpoklady  
  
1. Otevřete manifest aplikace ( *.manifest* souboru) pro vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace v textovém editoru.  
  
2. Předpoklad pro provedení operačního systému, přidejte `supportUrl` atribut `dependentOS` element:  
  
   ```xml  
    <dependency>  
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
         <osVersionInfo>  
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
         </osVersionInfo>  
       </dependentOS>  
     </dependency>  
   ```  
  
3. Předpokladem pro verzi modulu common language runtime, přidejte `supportUrl` atribut `dependentAssembly` položku, která určuje společné závislosti modulu runtime jazyka:  
  
   ```xml  
     <dependency>  
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
       </dependentAssembly>  
     </dependency>  
   ```  
  
4. Předpokladem pro sestavení, které musí být předinstalován v globální mezipaměti sestavení, nastavte `supportUrl` pro `dependentAssembly` element, který určuje požadované sestavení:  
  
   ```xml  
     <dependency>  
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
       </dependentAssembly>  
     </dependency>  
   ```  
  
5. Volitelné. U aplikací určených pro rozhraní .NET Framework 4, otevření manifestu nasazení ( *.application* souboru) pro vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace v textovém editoru.  
  
6. Součásti rozhraní .NET Framework 4, přidejte `supportUrl` atribut `compatibleFrameworks` element:  
  
   ```xml  
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
   </compatibleFrameworks>  
   ```  
  
7. Jakmile jste ručně změnili manifest aplikace, musíte znovu podepsat manifest aplikace pomocí digitálního certifikátu, a aktualizovat a znovu podepsat manifest nasazení. Použití *Mage.exe* nebo *MageUI.exe* nástroje sady SDK a provést tuto úlohu jako obnovení těchto souborů pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vymaže ručně provedené změny. Další informace o použití Mage.exe k opětovnému podepsání manifestů naleznete v tématu [postupy: opětovné podepsání aplikace a manifesty nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework  
 Adresa URL podpory se nezobrazí v dialogovém okně, pokud aplikace je označen ke spuštění v částečném vztahu důvěryhodnosti.  
  
## <a name="see-also"></a>Viz také:  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > – element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Nezbytné součásti pro nasazení aplikace](../deployment/application-deployment-prerequisites.md)