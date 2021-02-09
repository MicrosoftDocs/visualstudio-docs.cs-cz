---
title: Vystavení typů pro vizuální návrháře | Microsoft Docs
description: Naučte se vystavit definice tříd a typů, včetně těch ve vlastních nástrojích, aby je Visual Studio mohly zpřístupnit vizuálním návrhářům.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c36552c3a10f4ddbf50a7a28978acf27118bbd34
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887091"
---
# <a name="expose-types-to-visual-designers"></a>Vystavení typů pro vizuální návrháře
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pro zobrazení vizuálního návrháře musí mít přístup k třídám a definicím typu v době návrhu. Třídy jsou načteny z předdefinované sady sestavení, které zahrnují kompletní sadu závislostí aktuálního projektu (odkazy plus jejich závislosti). Může být také nutné, aby vizuální návrháři mohli přistupovat ke třídám a typům, které jsou definovány v souborech generovaných vlastními nástroji.

 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]Systémy a [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektový systém poskytují podporu pro přístup k vygenerovaným třídám a typům prostřednictvím dočasných přenosných spustitelných souborů (dočasné rozhraní pes). Jakýkoli soubor generovaný vlastním nástrojem lze zkompilovat do dočasného sestavení tak, aby mohly být z těchto sestavení načteny typy a zpřístupněny pro návrháře. Výstup každého vlastního nástroje je zkompilován do samostatného dočasného prostředí PE a úspěch nebo neúspěch této dočasné kompilace závisí pouze na tom, zda lze vygenerovaný soubor zkompilovat. I když se projekt nemusí sestavit jako celek, může být pro návrháře stále k dispozici individuální dočasný přístup k nim.

 Systém projektu poskytuje úplnou podporu pro sledování změn ve výstupním souboru vlastního nástroje za předpokladu, že tyto změny jsou výsledkem spuštění vlastního nástroje. Pokaždé, když se spustí vlastní nástroj, vygeneruje se nový dočasný PE a do návrháře se odešlou příslušná oznámení.

> [!NOTE]
> Vzhledem k tomu, že se soubor generace dočasné spustitelné aplikace stane na pozadí, žádné chyby nejsou hlášeny uživateli, pokud kompilace dojde k chybě.

 Vlastní nástroje, které využívají podporu dočasného prostředí PE, musí splňovat následující pravidla:

- **GeneratesDesignTimeSource** musí být v registru nastavené na hodnotu 1.

     Žádná kompilace spustitelného souboru programu neproběhne bez tohoto nastavení.

- Vygenerovaný kód musí být ve stejném jazyce jako globální nastavení projektu.

     Dočasné prostředí PE je kompilováno bez ohledu na to, co vlastní nástroj hlásí jako požadované rozšíření v systému <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> za předpokladu, že **GeneratesDesignTimeSource** je v registru nastaveno na hodnotu 1. Přípona nemusí být *. vb*, *. cs* nebo *. jsl*; může to být jakékoli rozšíření.

- Kód generovaný vlastním nástrojem musí být platný a musí být zkompilován sám s použitím pouze sady odkazů přítomných v projektu v době, kdy je <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> dokončeno.

     Když je kompilováno dočasné prostředí PE, jediný zdrojový soubor poskytnutý kompilátoru je výstup vlastního nástroje. Proto vlastní nástroj, který používá dočasné prostředí PE, musí generovat výstupní soubory, které mohou být kompilovány nezávisle na jiných souborech v projektu.

## <a name="see-also"></a>Viz také
- [Úvod do objektu BuildManager](/previous-versions/8f9kffa8(v=vs.140))
- [Implementace generátorů tvořených jedním souborem](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrovat generátory jednoho souboru](../../extensibility/internals/registering-single-file-generators.md)