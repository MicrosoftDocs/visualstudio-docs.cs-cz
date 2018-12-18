---
title: Požadavky na nasazení aplikací | Dokumentace Microsoftu
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
manager: wpickett
ms.openlocfilehash: e382c5d312a2de69281bdeda92e9c275e2877932
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890988"
---
# <a name="application-deployment-prerequisites"></a>Nezbytné součásti nasazení aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K zajištění, že vaše aplikace se nainstaluje a úspěšně spuštěn, je nutné nejdříve zkontrolovat, že jsou na cílovém počítači již nainstalovány všechny součásti, na kterých vaše aplikace je závislá. Například většina aplikace vytvořené s použitím [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jsou závislé [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]; správnou verzi modulu common language runtime musí existovat v cílovém počítači před instalací aplikace.  
  
 Můžete vybrat tyto požadavky **dialogové okno požadavky** a nainstalovat rozhraní .NET Framework a další distribuovatelné součásti jako součást instalace. Tento postup se označuje jako *spuštění*. Dále [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vygeneruje spustitelný program Windows s názvem Setup.exe, označované také jako *zaváděcí nástroj*. Zaváděcí nástroj je odpovědný za instalaci těchto nezbytných podmínkách před spuštěním vaší aplikace. Další informace o výběru těchto nezbytných podmínkách naleznete v tématu [dialogové okno požadavky](../ide/reference/prerequisites-dialog-box.md).  
  
 Každý požadavek je balíček zaváděcího nástroje. Balíček zaváděcího nástroje je skupina adresářů a souborů, které obsahují soubory manifestu, které popisují, jak by měly být nainstalovány kontrolu požadovaných součástí. Pokud vaše aplikace požadavky nejsou uvedené v **požadovaných součástí dialogovému oknu**, můžete vytvořit vlastní balíčky zaváděcího nástroje a přidat je do sady Visual Studio. Potom můžete vybrat požadované součásti v **dialogové okno požadavky**. Další informace najdete v tématu [vytváření balíčků Bootstrapperu](../deployment/creating-bootstrapper-packages.md).  
  
 Ve výchozím nastavení spuštění je povolen pro nasazení ClickOnce. Zaváděcí nástroj vygeneruje pro nasazení ClickOnce je podepsán. Probíhá spuštění pro komponentu můžete zakázat, ale měli byste tak činit pouze v případě, že jste si jisti, že je již nainstalována správná verze komponenty na všech cílových počítačích.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Spuštění a nasazení ClickOnce  
 Před instalací aplikace na klientském počítači [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se zaměřuje klienta a ujistěte se, že mají určité požadavky uvedenými v manifestu aplikace. Patří mezi ně například:  
  
- Minimální požadovaná verze common language runtime, který je zadán jako závislost sestavení v manifestu aplikace.  
  
- Minimální požadovaná verze operačního systému Windows požadované aplikací, jak je uvedeno v aplikaci manifestu pomocí `<osVersionInfo>` elementu. (Viz [ \<závislost > Element](../deployment/dependency-element-clickonce-application.md))  
  
- Minimální verze všech sestavení, které musí být předinstalován v globální mezipaměti sestavení (GAC), jak jsou určené deklarace závislost sestavení v manifestu sestavení.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rozpozná chybějící požadované součásti a požadavky můžete nainstalovat pomocí zaváděcí nástroj. Další informace najdete v tématu [postupy: instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Chcete-li změnit hodnoty v manifestech vygenerovat pomocí nástrojů, jako [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a MageUI.exe, budete muset upravit manifest aplikace v textovém editoru a nové podepsání manifestů aplikace a nasazení. Další informace najdete v tématu [postupy: opětovné podepsání aplikace a manifesty nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Pokud používáte Visual Studio a ClickOnce k nasazení vaší aplikace, balíčky zaváděcího nástroje, které jsou vybrány ve výchozím nastavení závisí na verzi rozhraní .NET Framework v řešení. Nicméně pokud změníte cílovou verzi rozhraní .NET Framework, je nutné aktualizovat možnosti v **dialogové okno požadavky** ručně.  
  
|Cílová verze .NET Frameworku|Balíčky zaváděcího nástroje vybrané|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalační služba systému Windows 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Instalační služba systému Windows 3.1|  
  
 S [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, stránku Publish.htm generovaných [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Průvodce publikováním odkazuje buď na odkaz, který nainstaluje pouze aplikace, nebo ke spojení, které instaluje aplikace a komponenty se spustil.  
  
 Pokud generujete zaváděcí nástroj s použitím Průvodce publikování ClickOnce nebo publikovat stránku v sadě Visual Studio, je automaticky přihlášen Setup.exe. Nicméně pokud chcete použít certifikát vašeho zákazníka k podepisování zaváděcí nástroj, se můžete přihlásit soubor později.  
  
## <a name="bootstrapping-and-msbuild"></a>Spuštění a nástroje MSBuild  
 Pokud nepoužijete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ale kompilace aplikace v příkazovém řádku, můžete vytvořit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] spuštění aplikace pomocí úlohy Microsoft Build Engine (MSBuild). Další informace najdete v tématu [GenerateBootstrapper – úloha](../msbuild/generatebootstrapper-task.md).  
  
 Jako alternativu k spuštění můžete předem nasadit komponenty použití distribuce systému elektronického software, jako je například Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty příkazového řádku zaváděcího nástroje (Setup.exe)  
 Setup.exe generovaný [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a úlohy nástroje MSBuild podporuje následující malý počet argumentů příkazového řádku. Všechny argumenty předány zaváděcí aplikace nad rámec těchto se předávají do aplikace Instalační služby.  
  
 Pokud změníte všechny možnosti zaváděcího nástroje, musíte změnit bez znaménka zaváděcí nástroj a pak se přihlaste na soubor zaváděcího nástroje později.  
  
|Argument příkazového řádku|Popis|  
|---------------------------|-----------------|  
|**-?, -h, – Nápověda**|Zobrazí dialogové okno nápovědy.|  
|**– Adresa url, - componentsurl**|Zobrazí uloženou adresu URL a adresu url komponent pro toto nastavení.|  
|**-url =** `location`|Nastaví adresu URL, kde bude hledat Setup.exe [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.|  
|**-componentsurl =** `location`|Nastaví adresu URL, kde Setup.exe bude hledat závislosti, jako [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|  
|**-homesite =** `true`**&#124;** `false`|Když `true`, stahuje závislosti z preferované umístění na webu dodavatele. Přepíše se tím požadavek **- componentsurl** nastavení. Když `false`, soubory ke stažení závislostí v adrese URL zadané hodnotou **- componentsurl**.|  
  
## <a name="operating-system-support"></a>Podpora operačního systému  
 Zaváděcí nástroj Visual Studio není podporována v systému Windows Server 2008 Server Core nebo Windows Server 2008 R2 Server Core, který bude poskytovat prostředí nízká údržba serveru s omezenou funkčností. Možnost instalace jádra serveru podporuje například pouze profilu rozhraní .NET Framework 3.5 Server Core, takže funkcemi sady Visual Studio, které jsou závislé na úplné rozhraní .NET Framework nelze spustit.  
  
## <a name="see-also"></a>Viz také  
 [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)



