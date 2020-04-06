---
title: Glygová kontrola (správa zdrojového kódu VSPackage) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708319"
---
# <a name="glyph-control-source-control-vspackage"></a>Glyf control (správa zdrojového kódu VSPackage)
Součástí hluboké integrace, která je k dispozici pro správou zdrojového kódu VSPackages je možnost zobrazit své vlastní glyfy k označení stavu položek pod správou zdrojového kódu.

## <a name="levels-of-glyph-control"></a>Úrovně kontroly glyfů
 Glyf stavu je ikona, která označuje aktuální stav položky při zobrazení, například v **Průzkumníku řešení** nebo v **zobrazení třídy**. Zdroj ovládacího prvku VSPackage můžete vykonávat dvě úrovně glyfů řízení. Může omezit výběr glyfů na předdefinovanou sadu glyfů poskytovaných [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ide nebo může definovat vlastní sadu glyfů, které mají být zobrazeny.

### <a name="default-set-of-glyphs"></a>Výchozí sada glyfů
 Chcete-li zjistit stav glyfy, které jsou přidruženy k položce v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> **Průzkumníku řešení**, projekt požaduje stav glyf ze správy zdrojového kódu pomocí . Zdroj ovládacíprvek VSPackage může rozhodnout zachovat výběr glyfů omezena na předdefinované glyfy poskytované IDE. V tomto případě VSPackage předá zpět pole hodnot představující výčty glyfů, které jsou definovány v *vsshell.idl*. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Toto je předdefinovaná sada glyfů nastavená ide, jako je například visací zámek pro rekostkovaný glyf a zaškrtnutí souboru glyfů zaškrtnuté.

### <a name="custom-set-of-glyphs"></a>Vlastní sada glyfů
 Zdrojové správě VSPackage můžete použít své vlastní glyfy pro jedinečný vzhled a chování při instalaci. Když je aktivní nový zdrojový ovládací prvek VSPackage, měl by být schopen začít používat vlastní glyfy i v případě, že předchozí zdrojový prvek VSPackage je stále načten, ale neaktivní. V tomto režimu ovládacího prvku zdrojového kódu VSPackage stále můžete [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] použít existující ikony k zachování vzhled konzistentní s, pokud se rozhodne.

 Služba <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> podporuje rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, které vspackage volitelně implementovat a které budou požádáni o ide. Když rozhraní IDE provede [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] požadavek, se zase pokusí získat toto rozhraní z aktuálně registrované ho správě zdrojového kódu VSPackage. Pokud rozhraní existuje v registrovaném balíčku VSPackage, požadavek ide pro vlastní glyfy proběhne úspěšně; v opačném [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] případě ide používá výchozí sadu glyfů.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> se používá [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] k získání seznamu obrázků zobrazujících různé stavy správy zdrojového kódu. Zdrojový ovládací prvek VSPackage vrátí do ide popisovač seznamu obrázků pro své vlastní glyfy. IDE vytvoří kopii seznamu obrázků v tomto okamžiku a později jej použije k výběru glyfů, které se mají zobrazit. Pokud nové rozhraní není podporováno nebo `IVsSccGlyphs::GetCustomGlyphList` metoda vrátí `E_NOTIMPL`, pak IDE získá své glyfy z výchozího seznamu glyfů dodaných . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
