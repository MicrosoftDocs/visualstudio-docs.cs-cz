---
title: O příponách názvů souborů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740356"
---
# <a name="about-file-name-extensions"></a>O příponách názvů souborů
Když zaregistrujete příponu souboru VSPackage, přidružíte ji k verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aplikace . To je důležité, pokud [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je v počítači nainstalována více než jedna verze programu.

 Přípony souborů pro VSPackages jsou registrovány pod **HKEY_CLASSES_ROOT** klíč s výchozí hodnotou, která odkazuje na přidružený programový identifikátor (ProgID).

 Následující příklad ukazuje informace o registraci přípony souboru *.vcproj:*

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 Soubory přidružené [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] k musí mít verzi ProgID, například `VisualStudio.vcproj.8.0`. Verze ProgID umožňuje souběžné instalace produktu udržovat přidružení přípony souborů mezi verzemi produktu. ProgID specifické pro verzi také umožňuje používat standardní slovesa, jako je například otevření, úpravy a tak dále, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]bez obav z přepsání nebo přepsání jinými aplikacemi nebo verzemi aplikace .

 V některých případech progID spojené s příponou souboru by neměla být změněna. Například ProgID pro příponu *souboru HTM* (progid = htmlfile) je pevně zakódován na mnoha místech v operačním systému a je široce známý a používaný ve spojení se soubory *HTM* a *.html.*

## <a name="see-also"></a>Viz také
- [Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Určení obslužných rutin souborů pro přípony názvů souborů](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
