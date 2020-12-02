---
title: Ovládací prvek glyf (VSPackage správy zdrojového kódu) | Microsoft Docs
description: Naučte se, jak zobrazit vlastní glyfy v balíčku VSPackage správy zdrojového kódu, abyste mohli použít vlastní ikony k indikaci stavu položek pod správou zdrojových kódů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eaf7f40224e2f197627bb995dc6cccdf297b46e5
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480470"
---
# <a name="glyph-control-source-control-vspackage"></a>Ovládací prvek glyf (VSPackage správy zdrojového kódu)
Součástí hluboké integrace dostupného pro sadu VSPackage správy zdrojového kódu je schopnost zobrazit vlastní glyfy, které označují stav položek pod správou zdrojového kódu.

## <a name="levels-of-glyph-control"></a>Úrovně ovládacího prvku glyf
 Piktogram stavu je ikona, která označuje aktuální stav položky při zobrazení, například v **Průzkumník řešení** nebo v **zobrazení tříd**. VSPackage správy zdrojového kódu může vyvolávat dvě úrovně ovládacího prvku glyf. Může omezit volbu glyfů na předdefinovanou sadu glyfů poskytovaných [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE nebo může definovat vlastní sadu glyfů, které se mají zobrazit.

### <a name="default-set-of-glyphs"></a>Výchozí sada glyfů
 Chcete-li určit glyfy stavu, které jsou spojeny s položkou v **Průzkumník řešení**, projekt požaduje glyf stavu ze správy zdrojového kódu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . VSPackage správy zdrojového kódu se může rozhodnout zachovat volbu glyfů omezených na předdefinované glyfy poskytované IDE. V tomto případě VSPackage předává zpět pole hodnot reprezentujících výčty glyfů, které jsou definovány v *vsshell. idl*. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Toto je předdefinovaná sada glyfů nastavená rozhraním IDE, jako je například visacího zámku nezobrazuje pro glyfy vrácených se změnami a zaškrtávací značka pro vyhradit glyf.

### <a name="custom-set-of-glyphs"></a>Vlastní sada glyfů
 VSPackage správy zdrojového kódu může použít vlastní glyfy pro jedinečný vzhled a chování při jeho instalaci. Když je aktivní nový prvek VSPackage správy zdrojového kódu, měl by být schopný začít používat jeho vlastní glyfy i v případě, že je ještě načten předchozí ovládací prvek VSPackage zdrojového kódu, ale neaktivní. V tomto režimu může model VSPackage správy zdrojového kódu stále používat stávající ikony, aby bylo možné zachovat vzhled konzistentní s tím, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] že se rozhodne.

 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>Služba podporuje rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> které VSPackage může volitelně implementovat a které bude požádáno o rozhraní IDE. Když IDE vytvoří požadavek, pak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se znovu pokusí získat toto rozhraní z aktuálně registrovaného balíčku VSPackage pro správu zdrojového kódu. Pokud rozhraní existuje v registrované VSPackage, požadavek rozhraní IDE pro vlastní glyfy bude úspěšný. v opačném případě [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní IDE použije svou výchozí sadu glyfů.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>Metoda je používána nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] k získání seznamu obrázků zobrazujících různé stavy správy zdrojů. Správa zdrojového kódu se vrátí do integrovaného vývojového prostředí (IDE) a popisovač do seznamu obrázků pro vlastní glyfy. Rozhraní IDE vytvoří v tomto okamžiku kopii seznamu obrázků a použije ji později k výběru glyfů, které se mají zobrazit. Pokud nové rozhraní není podporováno nebo se `IVsSccGlyphs::GetCustomGlyphList` Metoda vrátí `E_NOTIMPL` , rozhraní IDE získá své glyfy z výchozího seznamu glyfů dodaných pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
