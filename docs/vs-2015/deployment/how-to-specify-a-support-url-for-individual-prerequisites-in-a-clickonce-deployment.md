---
title: 'Postupy: určení adresu URL podpory pro jednotlivé předpoklady v nasazení ClickOnce | Dokumentace Microsoftu'
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
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: bdd366cb8ac86f20e7457178f63aa553a0814158
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831572"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Postupy: Určení adresy URL webu s podporou pro jednotlivé předpoklady v nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] otestovat nasazení pro celou řadou požadavky, které musí být k dispozici v klientském počítači pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] spuštění aplikace. Patří mezi ně požadovanou minimální verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], verzi operačního systému a všechna sestavení, které musí být předinstalován v globální mezipaměti sestavení (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], však nemůže nainstalovat některý z těchto nezbytných podmínkách; Pokud není nalezen předpoklad, jednoduše zastaví instalaci a zobrazí dialogové okno s vysvětlením, proč se instalace nepovedla.  
  
 Existují dvě metody pro instalaci požadavků. Můžete nainstalovat pomocí aplikace zaváděcího nástroje. Alternativně můžete zadat adresu URL podpory pro jednotlivé předpoklady, které se zobrazí uživatelům na dialogové okno, pokud se nenajde kontrolu požadovaných součástí. Na stránce odkazuje tuto adresu URL může obsahovat odkazy na pokyny k instalaci požadované součásti. Pokud aplikace neuvádějí adresu URL podpory pro jednotlivé předpoklady [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zobrazí adresa URL podpory určená v manifestu nasazení pro aplikaci jako celek, pokud je definována.  
  
 Zatímco [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Mage.exe a MageUI.exe všechny slouží ke generování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, žádný z těchto nástrojů přímo nepodporuje zadání adresu URL podpory pro jednotlivé předpoklady. Tento dokument popisuje postup upravení vašeho nasazení manifest aplikace a manifest nasazení pro zahrnutí těchto podporují adresy URL.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Zadáte adresu URL podpory pro jednotlivé předpoklady  
  
1.  Otevření manifestu aplikace (soubor .manifest) pro vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace v textovém editoru.  
  
2.  Předpoklad pro provedení operačního systému, přidejte `supportUrl` atribut `dependentOS` element:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Předpokladem pro verzi modulu common language runtime, přidejte `supportUrl` atribut `dependentAssembly` položku, která určuje společné závislosti modulu runtime jazyka:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Předpokladem pro sestavení, které musí být předinstalován v globální mezipaměti sestavení, nastavte `supportUrl` pro `dependentAssembly` element, který určuje požadované sestavení:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Volitelné. U aplikací určených pro rozhraní .NET Framework 4, otevření manifestu nasazení (soubor .application) pro vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace v textovém editoru.  
  
6.  Součásti rozhraní .NET Framework 4, přidejte `supportUrl` atribut `compatibleFrameworks` element:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Jakmile jste ručně změnili manifest aplikace, musíte znovu podepsat manifest aplikace pomocí digitálního certifikátu, a aktualizovat a znovu podepsat manifest nasazení. Je nutné použít Mage.exe nebo MageUI.exe SDK nástrojů k provedení této úlohy, jako obnovení těchto souborů pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vymaže ručně provedené změny. Další informace o použití Mage.exe k opětovnému podepsání manifestů naleznete v tématu [postupy: opětovné podepsání aplikace a manifesty nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Adresa URL podpory se nezobrazí v dialogovém okně, pokud aplikace je označen ke spuštění v částečném vztahu důvěryhodnosti.  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > – Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)



