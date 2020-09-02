---
title: 'Postupy: určení adresy URL pro podporu pro jednotlivé předpoklady v nasazení ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679973"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Postupy: Určení adresy URL webu s podporou pro jednotlivé předpoklady v nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Nasazení může otestovat určitý počet požadavků, které musí být v klientském počítači k dispozici, aby bylo možné [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci spustit. Mezi ně patří požadovaná minimální verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , verze operačního systému a všechna sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]ale nemůže nainstalovat žádné z těchto nezbytných součástí. Pokud se požadovaná součást nenajde, jednoduše zastaví instalaci a zobrazí dialogové okno s vysvětlením, proč se instalace nezdařila.  
  
 Existují dvě metody pro instalaci požadovaných součástí. Můžete je nainstalovat pomocí aplikace zaváděcího nástroje. Případně můžete zadat adresu URL podpory pro jednotlivé požadavky, které se uživatelům zobrazí v dialogovém okně v případě, že požadovaná součást nebyla nalezena. Stránka odkazovaná adresou URL může obsahovat odkazy na pokyny pro instalaci požadované součásti. Pokud aplikace neurčí adresu URL podpory pro jednotlivou součást, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zobrazí adresu URL podpory určenou v manifestu nasazení aplikace jako celek, pokud je definována.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]K vygenerování nasazení se ale dají použít Mage.exe a MageUI.exe [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , žádný z těchto nástrojů přímo nepodporuje zadání adresy URL podpory pro jednotlivé požadavky. Tento dokument popisuje, jak upravit manifest aplikace nasazení a manifest nasazení tak, aby zahrnovaly tyto adresy URL podpory.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Určení adresy URL podpory pro jednotlivou součást  
  
1. Otevřete manifest aplikace (soubor. manifest) pro vaši [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci v textovém editoru.  
  
2. Pro předpoklad operačního systému přidejte `supportUrl` atribut do `dependentOS` elementu:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Pro předpoklad určité verze modulu CLR (Common Language Runtime) přidejte `supportUrl` atribut k `dependentAssembly` položce, která určuje závislost společného jazykového modulu runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Pro předpoklad pro sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC), nastavte `supportUrl` pro `dependentAssembly` element, který určuje požadované sestavení:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. Nepovinný parametr. Pro aplikace cílené na .NET Framework 4 otevřete manifest nasazení (soubor. Application) pro vaši [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci v textovém editoru.  
  
6. Pro .NET Framework 4 požadavky přidejte `supportUrl` atribut do `compatibleFrameworks` elementu:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Až ručně změníte manifest aplikace, musíte manifest aplikace znovu podepsat pomocí digitálního certifikátu a pak taky aktualizovat a znovu podepsat manifest nasazení. K provedení této úlohy je nutné použít nástroje Mage.exe nebo MageUI.exe SDK, protože tyto soubory jsou znovu vygenerovány pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vymazání ručních změn. Další informace o použití Mage.exe k opětovnému podepisování manifestů naleznete v tématu [How to: resigning Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Adresa URL podpory se v dialogovém okně nezobrazí, pokud je aplikace označena jako spuštěná v částečném vztahu důvěryhodnosti.  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Objekt](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce a Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Požadavky nasazení aplikace](../deployment/application-deployment-prerequisites.md)
