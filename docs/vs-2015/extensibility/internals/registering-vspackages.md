---
title: Registrace VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157393"
---
# <a name="registering-vspackages"></a>Registrace balíčků VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spoléhá na soubory. pkgdef pro popis a vyhledání VSPackage. Soubor. pkgdef obsahuje všechny registrační informace, které by jinak byly přidány do systémového registru. Spravované sady VSPackage jsou registrovány přidáním atributů ke zdrojovému kódu a následným spuštěním [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) ve výsledném sestavení pro vygenerování souboru. pkgdef.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Specifikace umístění souboru balíčku VSPackage pro prostředí sady VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Popisuje cestu načítání pro VSPackage.  
  
 [Registrace a zrušení registrace rozšíření VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Vysvětluje, jak zaregistrovat VSPackage.  
  
 [Použití vlastního registračního atributu k registraci rozšíření](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Popisuje, jak vytvořit registrační manifest, který se dá použít k nasazení spravovaného balíčku VSPackage.
