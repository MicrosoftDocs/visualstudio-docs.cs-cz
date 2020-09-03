---
title: Adresa URL podpory pro předpoklady v nasazení ClickOnce
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf474e4926403a9475860bfdc620ee4a6860f8aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381727"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Postupy: určení adresy URL pro podporu pro jednotlivé předpoklady v nasazení ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Nasazení může otestovat určitý počet požadavků, které musí být v klientském počítači k dispozici, aby bylo možné [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci spustit. Tyto závislosti zahrnují požadovanou minimální verzi .NET Framework, verzi operačního systému a všechna sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ale nemůže nainstalovat žádné z těchto nezbytných součástí. Pokud se požadovaná součást nenajde, jednoduše zastaví instalaci a zobrazí dialogové okno s vysvětlením, proč se instalace nezdařila.

 Existují dvě metody pro instalaci požadovaných součástí. Můžete je nainstalovat pomocí aplikace zaváděcího nástroje. Případně můžete zadat adresu URL podpory pro jednotlivé požadavky, které se uživatelům zobrazí v dialogovém okně v případě, že požadovaná součást nebyla nalezena. Stránka odkazovaná adresou URL může obsahovat odkazy na pokyny pro instalaci požadované součásti. Pokud aplikace neurčí adresu URL podpory pro jednotlivou součást, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zobrazí adresu URL podpory určenou v manifestu nasazení aplikace jako celek, pokud je definována.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]K vygenerování nasazení se ale dají použít *Mage.exe*a *MageUI.exe* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , žádný z těchto nástrojů přímo nepodporuje zadání adresy URL podpory pro jednotlivé požadavky. Tento dokument popisuje, jak upravit manifest aplikace nasazení a manifest nasazení tak, aby zahrnovaly tyto adresy URL podpory.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Zadejte adresu URL podpory pro individuální požadavek.

1. Otevřete manifest aplikace (soubor *. manifest* ) pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci v textovém editoru.

2. Pro předpoklad operačního systému přidejte `supportUrl` atribut do `dependentOS` elementu:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Pro předpoklad určité verze modulu CLR (Common Language Runtime) přidejte `supportUrl` atribut k `dependentAssembly` položce, která určuje závislost společného jazykového modulu runtime:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Pro předpoklad pro sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC), nastavte `supportUrl` pro `dependentAssembly` element, který určuje požadované sestavení:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Nepovinný parametr. Pro aplikace cílené na .NET Framework 4 otevřete manifest nasazení (soubor *. Application* ) pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci v textovém editoru.

6. Pro .NET Framework 4 požadavky přidejte `supportUrl` atribut do `compatibleFrameworks` elementu:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Až ručně změníte manifest aplikace, musíte manifest aplikace znovu podepsat pomocí digitálního certifikátu a pak taky aktualizovat a znovu podepsat manifest nasazení. Pomocí nástrojů *Mage.exe* nebo *MageUI.exe* SDK můžete tuto úlohu provést, protože tyto soubory znovu vygenerujete pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vymazání vašich ručních změn. Další informace o použití Mage.exe k opětovnému podepisování manifestů naleznete v tématu [How to: resigning Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework
 Adresa URL podpory se v dialogovém okně nezobrazí, pokud je aplikace označena jako spuštěná v částečném vztahu důvěryhodnosti.

## <a name="see-also"></a>Viz také
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks> objekt](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)
- [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)