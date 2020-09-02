---
title: Registrace a zrušení registrace VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193821"
---
# <a name="registering-and-unregistering-vspackages"></a>Registrace a zrušení registrace rozšíření VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atributy můžete použít k registraci VSPackage, ale  
  
## <a name="registering-a-vspackage"></a>Registrace balíčku VSPackage  
 Pomocí atributů můžete řídit registraci spravovaných VSPackage. Všechny registrační informace jsou obsaženy v souboru. pkgdef. Další informace o registraci na základě souborů naleznete v tématu [CreatePkgDef Utility](../extensibility/internals/createpkgdef-utility.md).  
  
 Následující kód ukazuje, jak použít standardní registrační atributy k registraci sady VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Rušení registrace rozšíření  
 Pokud jste experimentování s velkým množstvím různých VSPackage a chcete je odebrat z experimentální instance, stačí spustit příkaz pro **obnovení** . Na úvodní stránce počítače vyhledejte **resetování experimentální instance sady Visual Studio** nebo spusťte tento příkaz z příkazového řádku:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Pokud chcete odinstalovat rozšíření, které jste nainstalovali do vývojové instance sady Visual Studio, přejděte na **nástroje, rozšíření a aktualizace**, Najděte rozšíření a klikněte na **odinstalovat**.  
  
 Pokud z nějakého důvodu neuspěje žádná z těchto metod při odinstalaci rozšíření, můžete zrušit registraci sestavení VSPackage z příkazového řádku následujícím způsobem:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)
