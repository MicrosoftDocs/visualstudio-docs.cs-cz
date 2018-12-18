---
title: Požadavky na nasazení aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 421092218cdeb889fe195917e46b123c73e7e1f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851800"
---
# <a name="application-deployment-prerequisites"></a>Nezbytné součásti nasazení aplikace

Pokud chcete, aby vaše aplikace k instalaci a spuštění úspěšně, nejprve nainstalujte všechny součásti, na kterých vaše aplikace je závislá na cílovém počítači. Například většiny aplikací vytvořených pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jsou závislé [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Správnou verzi CLR v tomto případě musí být k dispozici na cílovém počítači před instalací aplikace.  

 Můžete vybrat tyto požadavky **dialogové okno požadavky** a nainstalovat rozhraní .NET Framework a další distribuovatelné jako součást instalace. Tento postup se označuje jako *spuštění*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vygeneruje spustitelný program Windows s názvem *Setup.exe*, označované také jako *zaváděcí nástroj*. Zaváděcí nástroj je odpovědný za instalaci těchto nezbytných podmínkách před spuštěním vaší aplikace. Další informace o výběru těchto nezbytných podmínkách naleznete v tématu [dialogové okno požadavky](../ide/reference/prerequisites-dialog-box.md).  

 Každý požadavek je balíček zaváděcího nástroje. Balíček zaváděcího nástroje je skupina adresáře a soubory, které obsahují soubory manifestu, které popisují, jak jsou nainstalovány požadované součásti. Pokud vaše aplikace požadavky nejsou uvedené v **požadovaných součástí dialogovému oknu**, můžete vytvořit vlastní balíčky zaváděcího nástroje a přidat je do sady Visual Studio. Potom můžete vybrat požadované součásti v **dialogové okno požadavky**. Další informace najdete v tématu [vytváření balíčků bootstrapperu](../deployment/creating-bootstrapper-packages.md).  

 Ve výchozím nastavení spuštění je povolen pro nasazení ClickOnce. Zaváděcí nástroj vygeneruje pro nasazení ClickOnce je podepsán. Probíhá spuštění pro komponentu můžete zakázat, ale pouze v případě, že jste si jisti, že je již nainstalována správná verze komponenty na všech cílových počítačích.  

## <a name="bootstrapping-and-clickonce-deployment"></a>Spuštění a ClickOnce – nasazení  
 Před instalací aplikace na klientském počítači [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prozkoumá klienta a ujistěte se, že mají požadavky uvedenými v manifestu aplikace. Patří mezi ně následující požadavky:  

- Minimální požadovaná verze common language runtime, který je zadán jako závislost sestavení v manifestu aplikace.  

- Minimální požadovaná verze operačního systému Windows požadované aplikací, jak je uvedeno v aplikaci manifestu pomocí `<osVersionInfo>` elementu. (Viz [ \<závislost > element](../deployment/dependency-element-clickonce-application.md).)  

- Minimální verze všechna sestavení, která musí být předinstalován v globální mezipaměti sestavení (GAC), jak jsou určené deklarace závislost sestavení v manifestu sestavení.  

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rozpozná chybějící požadované součásti a požadavky můžete nainstalovat pomocí zaváděcí nástroj. Další informace najdete v tématu [postupy: instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  

> [!NOTE]
>  Chcete-li změnit hodnoty v manifestech vygenerovat pomocí nástrojů, jako [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a *MageUI.exe*, budete muset upravit manifest aplikace v textovém editoru a pak znovu podepisovat manifesty aplikace a nasazení. Další informace najdete v tématu [postupy: Opětovné podepisování manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  

 Pokud používáte Visual Studio a ClickOnce k nasazení vaší aplikace, balíčky zaváděcího nástroje, které jsou vybrány ve výchozím nastavení závisí na verzi rozhraní .NET Framework v řešení. Nicméně pokud změníte cílovou verzi rozhraní .NET Framework, je nutné aktualizovat možnosti v **dialogové okno požadavky** ručně.  

|Cílová verze .NET Frameworku|Balíčky zaváděcího nástroje vybrané|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalační služba systému Windows 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Instalační služba systému Windows 3.1|  

 S [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, *Publish.htm* generované stránky [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Průvodce publikováním body buď na odkaz, který nainstaluje pouze aplikace, nebo ke spojení, které instaluje aplikace a se spustil součásti.  

 Pokud generujete zaváděcí nástroj s použitím Průvodce publikování ClickOnce nebo publikovat stránku v sadě Visual Studio *Setup.exe* je automaticky přihlášen. Nicméně pokud chcete použít certifikát vašeho zákazníka k podepisování zaváděcí nástroj, se můžete přihlásit soubor později.  

## <a name="bootstrapping-and-msbuild"></a>Spuštění a nástroje MSBuild  
 Pokud nepoužijete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale spíše kompilace aplikace v příkazovém řádku, můžete vytvořit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spuštění aplikace pomocí úlohy Microsoft Build Engine (MSBuild). Další informace najdete v tématu [GenerateBootstrapper – úloha](../msbuild/generatebootstrapper-task.md).  

 Jako alternativu k spuštění můžete předem nasadit komponenty použití distribuce systému elektronického software, jako je například Systems Management Server (SMS).  

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty příkazového řádku zaváděcího nástroje (Setup.exe)  
 *Setup.exe* generovaných [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a úlohy nástroje MSBuild podporuje následující sadu argumentů příkazového řádku. Libovolné další argumenty jsou předány instalačním programem aplikace.  

 Pokud změníte všechny možnosti zaváděcí nástroj, musíte změnit bez znaménka zaváděcího nástroje a později podepsat soubor zaváděcí nástroj.  


| argument příkazového řádku | Popis |
| - | - |
| **-?, -h, – Nápověda** | Zobrazí dialogové okno nápovědy. |
| **– Adresa url, - componentsurl** | Zobrazí uloženou adresu URL a adresu url komponent pro toto nastavení. |
| **-url =** `location` | Nastaví adresu URL kde *Setup.exe* bude hledat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace. |
| **-componentsurl =** `location` | Nastaví adresu URL kde *Setup.exe* bude hledat závislosti, jako [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. |
| **-homesite =** `true`**&#124;** `false` | Když `true`, stahuje závislosti z preferované umístění na webu dodavatele. Toto nastavení potlačí **- componentsurl** nastavení. Když `false`, soubory ke stažení závislostí v adrese URL zadané hodnotou **- componentsurl**. |

## <a name="operating-system-support"></a>Podpora operačního systému  
 Zaváděcí nástroj Visual Studio se nepodporuje v systému Windows Server 2008 Server Core nebo Windows Server 2008 R2 Server Core, protože poskytují nízká údržba serveru prostředí s omezenou funkčností. Například možnost instalace jádra serveru podporuje pouze rozhraní .NET Framework 3.5 Server Core profil, který nelze spustit aplikaci Visual Studio funkce, které závisí na úplné rozhraní .NET Framework.  

## <a name="see-also"></a>Viz také:  
 [Volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)