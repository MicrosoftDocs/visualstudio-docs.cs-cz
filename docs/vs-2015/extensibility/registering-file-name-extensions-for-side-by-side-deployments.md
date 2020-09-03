---
title: Registrace přípon názvů souborů pro souběžná nasazení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 354b91dd1282df9726c1ee9c47f610b0dfdd9c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163699"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrace přípony názvů souborů pro nasazení vedle sebe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pro VSPackage nasazené v souběžném prostředí musíte registrovat přípony názvů souborů k přidružení souborů ke správné verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pokud nepoužíváte příponu názvu souboru specifickou pro verzi, umožňuje registrace uživatelům otevřít projekt a soubory položek projektu v příslušné verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přípony názvů souborů](../extensibility/about-file-name-extensions.md)  
 Popisuje, jak jsou zaregistrované přípony názvů souborů.  
  
 [Určení popisovačů souborů pro přípony názvů souborů](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Poskytuje informace o tom, jak registrovat aplikace, které mohou otevřít, upravit a podobně, konkrétní příponu názvu souboru.  
  
 [Registrace operací pro přípony názvů souborů](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Popisuje, jak registrovat operace.  
  
 [Správa přidružení souborů vedle sebe](../extensibility/managing-side-by-side-file-associations.md)  
 Popisuje, jak zpracovávat souběžné instalace, ve kterých [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] by měla být vyvolána konkrétní verze pro otevření souboru.  
  
## <a name="related-sections"></a>Související oddíly  
 [Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Popisuje problémy týkající se více verzí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a sady VSPackage během vývoje a nasazení pro koncové uživatele.
