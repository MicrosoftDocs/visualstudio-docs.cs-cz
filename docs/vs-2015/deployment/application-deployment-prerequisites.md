---
title: Požadavky na nasazení aplikací | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4945efddb91142ce04f5b117129428ec4a054fc3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824316"
---
# <a name="application-deployment-prerequisites"></a>Nezbytné součásti nasazení aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby se zajistilo, že se vaše aplikace nainstaluje a spustí úspěšně, musíte nejdřív zkontrolovat, jestli jsou na cílovém počítači nainstalované všechny komponenty, na kterých je vaše aplikace závislá. Například většina aplikací, které byly vytvořeny pomocí, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mají závislost na rozhraní [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ; před instalací aplikace musí být na cílovém počítači přítomna správná verze modulu CLR (Common Language Runtime).  
  
 Tyto požadavky můžete vybrat v **dialogovém okně předpoklady** a nainstalovat .NET Framework a další distribuovatelné součásti jako součást instalace. Tento postup se označuje jako *spouštěcí*. Dále [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vygeneruje spustitelný program systému Windows s názvem Setup.exe, označovaný také jako *zaváděcí nástroj*. Zaváděcí nástroj zodpovídá za instalaci těchto požadavků ještě před spuštěním vaší aplikace. Další informace o výběru těchto požadavků najdete v [dialogovém okně předpoklady](../ide/reference/prerequisites-dialog-box.md).  
  
 Každá požadovaná součást je balíček zaváděcího nástroje. Balíček zaváděcího nástroje je skupina adresářů a souborů, které obsahují soubory manifestu, které popisují, jak by měla být požadovaná součást nainstalována. Pokud požadavky vaší aplikace nejsou uvedeny v **dialogovém okně požadovaná součást**, můžete vytvořit vlastní balíčky zaváděcího nástroje a přidat je do sady Visual Studio. Pak můžete vybrat požadované součásti v **dialogovém okně předpoklady**. Další informace najdete v tématu [vytváření balíčků zaváděcího nástroje](../deployment/creating-bootstrapper-packages.md).  
  
 Ve výchozím nastavení je pro nasazení ClickOnce povolený zaváděcí nástroj. Zaváděcí nástroj generovaný pro nasazení ClickOnce je podepsaný. Můžete zakázat spouštění pro komponentu, ale měli byste to udělat jenom v případě, že jste si jisti, že je na všech cílových počítačích už nainstalovaná správná verze součásti.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Zavedení a nasazení ClickOnce  
 Před instalací aplikace v klientském počítači zkontroluje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] klienta nástroje, aby zajistil, že obsahuje určité požadavky, které jsou zadány v manifestu aplikace. Patří mezi ně následující:  
  
- Minimální požadovaná verze modulu CLR (Common Language Runtime), která je zadána jako závislost sestavení v manifestu aplikace.  
  
- Minimální požadovaná verze operačního systému Windows, kterou vyžaduje aplikace, jak je uvedeno v manifestu aplikace pomocí `<osVersionInfo>` elementu. (Viz [ \<dependency> element](../deployment/dependency-element-clickonce-application.md))  
  
- Minimální verze všech a všech sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC), jak je uvedeno v deklaracích závislostí sestavení v manifestu sestavení.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dokáže detekovat chybějící požadované součásti a pomocí zaváděcího nástroje můžete nainstalovat požadované součásti. Další informace naleznete v tématu [How to: Install – požadavky s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
> Chcete-li změnit hodnoty v manifestech generovaných nástroji, jako jsou [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a MageUI.exe, je nutné upravit manifest aplikace v textovém editoru a poté znovu podepsat manifesty aplikace a nasazení. Další informace najdete v tématu [Postup: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Použijete-li aplikaci Visual Studio a ClickOnce k nasazení aplikace, jsou balíčky zaváděcího nástroje, které jsou vybrány ve výchozím nastavení, závislé na verzi .NET Framework v řešení. Pokud však změníte cílovou verzi .NET Framework, musíte ručně aktualizovat možnosti v **dialogovém okně předpoklady** .  
  
|Cílová .NET Framework|Vybrané balíčky zaváděcího nástroje|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalační služba systému Windows verze 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Instalační služba systému Windows verze 3.1|  
  
 Při [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení se stránka Publish.htm generovaná [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] průvodcem publikování odkazuje buď na odkaz, který nainstaluje jenom aplikaci, nebo na odkaz, který nainstaluje aplikaci i nasazené komponenty.  
  
 Pokud vygenerujete zaváděcí nástroj pomocí Průvodce publikováním ClickOnce nebo stránku publikovat v aplikaci Visual Studio, Setup.exe je automaticky podepsán. Pokud ale chcete použít certifikát zákazníka k podepsání zaváděcího nástroje, můžete ho později podepsat.  
  
## <a name="bootstrapping-and-msbuild"></a>Zavádění a MSBuild  
 Pokud nepoužíváte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ale zkompilujete své aplikace na příkazovém řádku, můžete vytvořit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] spouštěcí aplikaci pomocí úlohy Microsoft Build Engine (MSBuild). Další informace najdete v tématu [GenerateBootstrapper – Task](../msbuild/generatebootstrapper-task.md).  
  
 Jako alternativu ke spuštění nástroje můžete předem nasadit komponenty pomocí elektronického systému distribuce softwaru, jako je například Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty příkazového řádku pro zaváděcí nástroj (Setup.exe)  
 Setup.exe generovaný nástrojem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a úkoly nástroje MSBuild podporují následující malou sadu argumentů příkazového řádku. Všechny argumenty dodané do zaváděcí aplikace nad rámec těchto jsou předány instalačnímu programu aplikace.  
  
 Pokud změníte jakékoli možnosti zaváděcího nástroje, musíte změnit nepodepsaný zaváděcí nástroj a pak soubor zaváděcího nástroje podepsat později.  
  
|Argument příkazového řádku|Popis|  
|---------------------------|-----------------|  
|**-?,-h,-help**|Zobrazí dialogové okno s nápovědě.|  
|**-URL,-componentsurl**|Zobrazuje uloženou adresu URL a adresu URL komponent pro toto nastavení.|  
|**-URL =**`location`|Nastaví adresu URL, kam bude Setup.exe hledat [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci.|  
|**-componentsurl =**`location`|Nastaví adresu URL, kam bude Setup.exe Hledat závislosti, jako je například [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|  
|**-HomeSite =** `true` **&#124;**`false`|Když `true` aplikace stáhne závislosti z upřednostňovaného umístění na webu dodavatele. Tím se přepíše nastavení **-componentsurl** . Při `false` stahování stáhne závislosti z adresy URL určené parametrem **-componentsurl**.|  
  
## <a name="operating-system-support"></a>Podpora operačního systému  
 Zaváděcí nástroj sady Visual Studio není podporován v jádru serveru Windows Server 2008 Server Core nebo Windows Server 2008 R2 Server Core, který poskytuje serverové prostředí s nízkou údržbou s omezenými funkcemi. Například možnost instalace jádra serveru podporuje jenom profil jádra serveru .NET Framework 3,5, takže funkce sady Visual Studio, které závisí na plném .NET Framework, nemůžou běžet.  
  
## <a name="see-also"></a>Viz také  
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)
