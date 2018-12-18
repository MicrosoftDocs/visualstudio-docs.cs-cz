---
title: Průvodce (. Soubor vsz) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0076e1ee7409486a3b7b86ccd0f46bcd02a54a5
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757880"
---
# <a name="wizard-vsz-file"></a>Soubor průvodce (.Vsz)

Integrované vývojové prostředí (IDE) používá soubory ke spuštění průvodce. Tyto soubory .vsz obsahují informace, které rozhraní IDE používá k určení, které průvodce k volání a jaké informace, které mají být předána do průvodce.

Souboru je verze soubor text ve formátu souboru .ini, který nemá žádné oddíly. Informace o ví, že rozhraní IDE jsou uložené na začátku souboru. To poskytuje připojení mezi průvodce, který volá rozhraní IDE a parametry, které jsou v souboru mají být předány rozhraní IDE. Zbytek souboru obsahuje parametry, které jsou specifické pro průvodce a které se mají shromáždit pomocí rozhraní IDE a předaný konkrétní průvodce.

Následující příklad ukazuje obsah souboru.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Toto jsou částí v souboru.

|Část|Popis|
|----------|-----------------|
|VSWizard|První parametr v souboru je číslo verze formátu souboru šablony. Toto číslo verze musí být 6.0, 7.0, 7.1 nebo 8.0. Další čísla nelze spustit a způsobit chybu neplatný formát.|
|Průvodce|Toto pole obsahuje OLE ProgID v průvodci, případně GUID řetězcovou reprezentaci CLSID průvodce, který je spoluvytvářen pomocí rozhraní IDE.|
|Param|Následující části jsou volitelné. Můžete přidat až potřebné.|

Parametry povolit předat další parametry vlastního průvodce .vsz Soubor. Každá hodnota je předán jako element řetězce v poli proměnných do průvodce. Další informace najdete v tématu [vlastní parametry](../../extensibility/internals/custom-parameters.md).

Chcete-li přidat výchozí ID národního prostředí do souboru, zadejte `FALLBACK_LCID`= xxxx, kde xxxx je ID národního prostředí, například 1033 pro angličtinu. Když `FALLBACK_LCID` parametr je definován, Průvodce používá ID národního prostředí zadané náhradní, pokud aktuální ID nebyl nalezen.

## <a name="see-also"></a>Viz také:

- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)