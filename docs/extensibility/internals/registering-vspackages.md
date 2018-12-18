---
title: Registrace VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6f7e603fbc023415ad2b8ddc157f239feb53768
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128842"
---
# <a name="registering-vspackages"></a>Registrace VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spoléhá na soubory .pkgdef popsat a vyhledejte VSPackage. Soubor .pkgdef obsahuje všechny informace o registraci, které by jinak bylo možné přidat do registru systému. Spravované VSPackages jsou registrované přidáním atributy ke zdrojovému kódu a pak spustit [CreatePkgDef nástroj](../../extensibility/internals/createpkgdef-utility.md) na výsledné sestavení můžete vytvořit soubor .pkgdef.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Specifikace umístění souboru balíčku VSPackage pro prostředí sady VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Popisuje cestu načítání pro VSPackages.  
  
 [Registrace a zrušení registrace rozšíření VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Vysvětluje, jak zaregistrovat VSPackage.  
