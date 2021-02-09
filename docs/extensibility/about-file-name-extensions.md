---
title: O příponách názvů souborů | Microsoft Docs
description: Naučte se, jak registrovat přípony názvů souborů pro VSPackage a přidružit je ke konkrétní verzi sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3f938eb31c06e1e88af21b058b4475bc192d49c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874406"
---
# <a name="about-file-name-extensions"></a>O příponách názvů souborů
Když zaregistrujete příponu souboru VSPackage, přidružíte ji k verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . To je důležité [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , pokud je v počítači nainstalována více než jedna verze systému.

 Přípony souborů pro VSPackage jsou registrovány v **HKEY_CLASSES_ROOT** klíč s výchozí hodnotou, která odkazuje na příslušný programový identifikátor (ProgID).

 Následující příklad ukazuje informace o registraci pro příponu souboru *. vcproj* :

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Soubory přidružené k [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musí mít identifikátor ProgID s verzí, jako je například `VisualStudio.vcproj.8.0` . Identifikátor ProgID s verzí umožňuje souběžné instalace produktu zachovat přidružení přípon souborů mezi verze produktu. Identifikátor ProgID specifický pro verzi také umožňuje používat standardní příkazy, jako je například otevřít, upravit a tak dále, bez obav o přepsání nebo přepsání jinými aplikacemi nebo verzemi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 V některých případech by identifikátor ProgID přidružený k příponě souboru neměl být změněn. Například ProgID pro příponu souboru *. htm* (ProgID = htmlfile) je pevně zakódována v řadě míst v operačním systému a je široce známá a používána v asociaci se soubory *. htm* a *. html* .

## <a name="see-also"></a>Viz také
- [Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Zadat obslužné rutiny souborů pro přípony názvů souborů](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
