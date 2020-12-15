---
title: Průvodce (. Vsz) | Microsoft Docs
description: Přečtěte si o souborech. vsz, které IDE používá ke spouštění průvodců. Soubory obsahují informace o tom, který průvodce má zavolat a co má průvodce předat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fe32028f271d02dd518509bb86906197e6acb4e
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487735"
---
# <a name="wizard-vsz-file"></a>Soubor průvodce (.Vsz)

Integrované vývojové prostředí (IDE) používá k zahájení průvodců soubory. vsz. Tyto soubory. vsz obsahují informace, které rozhraní IDE používá k určení, který průvodce má zavolat a jaké informace mají předat průvodce.

Soubor. vsz je verze textového souboru ve formátu. ini, který neobsahuje žádné oddíly. Informace známé rozhraním IDE jsou uloženy na začátku souboru. To poskytuje odkaz mezi průvodcem, který rozhraní IDE volá, a parametry, které jsou v souboru. vsz, které mají být předány do rozhraní IDE. Zbytek souboru poskytuje parametry, které jsou specifické pro průvodce a které mají být shromažďovány rozhraním IDE a předány do konkrétního průvodce.

Následující příklad ukazuje obsah souboru. vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Níže jsou uvedené části souboru. vsz.

|Část|Popis|
|----------|-----------------|
|VSWizard|První parametr v souboru je číslo verze formátu souboru šablony. Toto číslo verze musí být 6,0, 7,0, 7,1 nebo 8,0. Nelze spustit jiné počty a způsobit chybu neplatného formátu.|
|Tip|Toto pole obsahuje identifikátor ProgID OLE průvodce nebo případně řetězcovou reprezentaci identifikátoru CLSID průvodce, který je vytvářen pomocí rozhraní IDE.|
|Param|Tyto části jsou volitelné. Podle potřeby můžete přidat tolik, kolik potřebujete.|

Parametry umožňují souboru. vsz předat do průvodce další vlastní parametry. Každá hodnota je předána jako prvek řetězce v poli variant průvodce. Další informace najdete v tématu [vlastní parametry](../../extensibility/internals/custom-parameters.md).

Pokud chcete do souboru. vsz přidat výchozí ID národního prostředí, zadejte `FALLBACK_LCID` = xxxx, kde xxxx je ID národního prostředí, například 1033 pro angličtinu. Pokud `FALLBACK_LCID` je definován parametr, použije průvodce zadané ID záložního národního prostředí, pokud nebylo nalezeno aktuální ID.

## <a name="see-also"></a>Viz také

- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubory popisu adresáře šablon (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
