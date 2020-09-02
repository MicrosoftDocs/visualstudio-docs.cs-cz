---
title: O příponách názvů souborů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148037"
---
# <a name="about-file-name-extensions"></a>Přípony názvů souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když zaregistrujete příponu souboru VSPackage, přidružíte ji k verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . To je důležité [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , pokud je v počítači nainstalována více než jedna verze systému.  
  
 Přípony souborů pro VSPackage jsou registrovány v HKEY_CLASSES_ROOT klíč s výchozí hodnotou, která odkazuje na příslušný programový identifikátor (ProgID).  
  
 Následuje příklad registračních informací pro příponu souboru. vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 Soubory přidružené k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] musí mít identifikátor ProgID s verzí, například `VisualStudio.vcproj.8.0` , aby bylo možné souběžné instalace produktu zachovat přidružení přípon souborů mezi verzemi produktu. Identifikátor ProgID specifický pro verzi také umožňuje používat standardní příkazy, jako je například otevřít, upravit a tak dále, bez obav o přepsání nebo přepsání jinými aplikacemi nebo verzemi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 V některých případech by identifikátor ProgID přidružený k příponě souboru neměl být změněn. Například ProgID pro příponu souboru. htm (ProgID = htmlfile) je pevně zakódována v řadě míst v operačním systému a je široce známá a používána v asociaci se soubory. htm a. html.  
  
## <a name="see-also"></a>Viz také  
 [Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Určení popisovačů souborů pro přípony názvů souborů](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
