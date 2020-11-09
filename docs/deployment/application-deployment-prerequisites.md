---
title: Požadavky na nasazení aplikací | Microsoft Docs
description: Seznamte se s požadavky na nasazení pro vaše aplikace, včetně použití dialogového okna předpoklady a balíčků zaváděcího nástroje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c87b0f6ded2960054cb553dbeb85681aa447668b
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383245"
---
# <a name="application-deployment-prerequisites"></a>Nezbytné součásti nasazení aplikace

Chcete-li aplikaci nainstalovat a spustit úspěšně, nejprve nainstalujte všechny součásti, na kterých je vaše aplikace závislá, na cílový počítač. Například většina aplikací [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , které byly vytvořeny pomocí, má závislost na .NET Framework. V takovém případě musí být v cílovém počítači před instalací aplikace přítomna správná verze modulu CLR (Common Language Runtime).

 Tyto požadavky můžete vybrat v **dialogovém okně předpoklady** a nainstalovat .NET Framework a další distribuovatelné součásti jako součást instalace. Tento postup se označuje jako *spouštěcí*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vygeneruje spustitelný program systému Windows s názvem *Setup.exe* , označovaný také jako *zaváděcí nástroj*. Zaváděcí nástroj zodpovídá za instalaci těchto požadavků ještě před spuštěním vaší aplikace. Další informace o výběru těchto požadavků najdete v [dialogovém okně předpoklady](../ide/reference/prerequisites-dialog-box.md).

 Každá požadovaná součást je balíček zaváděcího nástroje. Balíček zaváděcího nástroje je skupina adresářů a souborů, které obsahují soubory manifestu, které popisují, jak jsou požadavky nainstalovány. Pokud požadavky vaší aplikace nejsou uvedeny v **dialogovém okně požadovaná součást** , můžete vytvořit vlastní balíčky zaváděcího nástroje a přidat je do sady Visual Studio. Pak můžete vybrat požadované součásti v **dialogovém okně předpoklady**. Další informace najdete v tématu [Vytvoření balíčků zaváděcího nástroje](../deployment/creating-bootstrapper-packages.md).

 Ve výchozím nastavení je pro nasazení ClickOnce povolený zaváděcí nástroj. Zaváděcí nástroj generovaný pro nasazení ClickOnce je podepsaný. Můžete zakázat spouštění pro součást, ale pouze v případě, že jste si jisti, že je na všech cílových počítačích již nainstalována správná verze součásti.

## <a name="bootstrapping-and-clickonce-deployment"></a>Zavedení a nasazení ClickOnce
 Před instalací aplikace na klientský počítač [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zkontroluje klienta, zda obsahuje požadavky zadané v manifestu aplikace. Mezi ně patří následující požadavky:

- Minimální požadovaná verze modulu CLR (Common Language Runtime), která je zadána jako závislost sestavení v manifestu aplikace.

- Minimální požadovaná verze operačního systému Windows, kterou vyžaduje aplikace, jak je uvedeno v manifestu aplikace pomocí `<osVersionInfo>` elementu. (Viz [ \<dependency> element](../deployment/dependency-element-clickonce-application.md).)

- Minimální verze všech sestavení, která musí být předinstalována v globální mezipaměti sestavení (GAC), jak je uvedeno v deklaracích závislostí sestavení v manifestu sestavení.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dokáže detekovat chybějící požadované součásti a pomocí zaváděcího nástroje můžete nainstalovat požadované součásti. Další informace naleznete v tématu [How to: Install – požadavky s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> Chcete-li změnit hodnoty v manifestech generovaných nástroji, jako jsou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a *MageUI.exe* , je nutné upravit manifest aplikace v textovém editoru a poté znovu podepsat manifesty aplikace a nasazení. Další informace najdete v tématu [Postup: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Použijete-li aplikaci Visual Studio a ClickOnce k nasazení aplikace, jsou balíčky zaváděcího nástroje, které jsou vybrány ve výchozím nastavení, závislé na verzi .NET Framework v řešení. Pokud však změníte cílovou verzi .NET Framework, musíte ručně aktualizovat možnosti v **dialogovém okně předpoklady** .

|Cílová .NET Framework|Vybrané balíčky zaváděcího nástroje|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalační služba systému Windows verze 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Instalační služba systému Windows verze 3.1|

 Při [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení se stránka *Publish.htm* generovaná [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] průvodcem publikování odkazuje buď na odkaz, který nainstaluje jenom aplikaci, nebo na odkaz, který nainstaluje aplikaci i nasazené komponenty.

 Pokud vygenerujete zaváděcí nástroj pomocí Průvodce publikováním ClickOnce nebo stránku publikovat v aplikaci Visual Studio, *Setup.exe* je automaticky podepsán. Pokud ale chcete použít certifikát zákazníka k podepsání zaváděcího nástroje, můžete ho později podepsat.

## <a name="bootstrapping-and-msbuild"></a>Zavádění a MSBuild
 Pokud nepoužíváte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ale raději zkompilujete své aplikace na příkazovém řádku, můžete vytvořit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spouštěcí aplikaci pomocí úlohy Microsoft Build Engine (MSBuild). Další informace najdete v tématu [GenerateBootstrapper – Task](../msbuild/generatebootstrapper-task.md).

 Jako alternativu ke spuštění nástroje můžete předem nasadit komponenty pomocí elektronického systému distribuce softwaru, jako je například Microsoft Systems Management Server (SMS).

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty příkazového řádku zaváděcího nástroje (Setup.exe)
 *Setup.exe* generovaný nástrojem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a úkoly nástroje MSBuild podporují následující sadu argumentů příkazového řádku. Všechny ostatní argumenty jsou předávány instalačnímu programu aplikace.

 Pokud změníte jakékoli možnosti zaváděcího nástroje, musíte změnit nepodepsaný zaváděcí nástroj a později podepsat soubor zaváděcího nástroje.

| Argument příkazového řádku | Popis |
| - | - |
| **-?,-h,-help** | Zobrazí dialogové okno s nápovědě. |
| **-URL,-componentsurl** | Zobrazuje uloženou adresu URL a adresu URL komponent pro toto nastavení. |
| **-URL =**`location` | Nastaví adresu URL, kam bude *Setup.exe* hledat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci. |
| **-componentsurl =**`location` | Nastaví adresu URL, kam bude *Setup.exe* Hledat závislosti, jako je například .NET Framework. |
| **-HomeSite =** `true` **&#124;**`false` | Když `true` aplikace stáhne závislosti z upřednostňovaného umístění na webu dodavatele. Toto nastavení přepisuje nastavení **-componentsurl** . Při `false` stahování stáhne závislosti z adresy URL určené parametrem **-componentsurl**. |

## <a name="operating-system-support"></a>Podpora operačního systému
 Zaváděcí nástroj sady Visual Studio není podporován v jádru serveru Windows Server 2008 nebo Windows Server 2008 R2 Server Core, protože poskytují serverové prostředí s nízkou údržbou s omezenými funkcemi. Například možnost instalace jádra serveru podporuje jenom profil jádra serveru .NET Framework 3,5, který nemůže spouštět funkce sady Visual Studio, které závisí na plném .NET Framework.

## <a name="see-also"></a>Viz také
- [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)