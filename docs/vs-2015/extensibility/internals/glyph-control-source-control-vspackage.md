---
title: Ovládací prvek glyf (VSPackage správy zdrojového kódu) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0960209b67c8d2f111296840119807d95bb2e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538418"
---
# <a name="glyph-control-source-control-vspackage"></a>Správa piktogramů (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Součástí hluboké integrace dostupného pro sadu VSPackage správy zdrojového kódu je schopnost zobrazit vlastní glyfy, které označují stav položek pod správou zdrojového kódu.  
  
## <a name="levels-of-glyph-control"></a>Úrovně ovládacího prvku glyf  
 Piktogram stavu je ikona, která označuje aktuální stav položky při zobrazení, například v **Průzkumník řešení** nebo v **zobrazení tříd**. VSPackage správy zdrojového kódu může vyvolávat dvě úrovně ovládacího prvku glyf. Může omezit volbu glyfů na předdefinovanou sadu glyfů poskytovaných [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE nebo může definovat vlastní sadu glyfů, které se mají zobrazit.  
  
### <a name="default-set-of-glyphs"></a>Výchozí sada glyfů  
 Chcete-li určit glyfy stavu, které jsou spojeny s položkou v **Průzkumník řešení**, projekt požaduje glyf stavu ze správy zdrojového kódu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . VSPackage správy zdrojového kódu se může rozhodnout zachovat volbu glyfů omezených na předdefinované glyfy poskytované IDE. V tomto případě VSPackage předává zpět pole hodnot reprezentujících výčty glyfů, které jsou definovány v vsshell. idl. Další informace najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Toto je předdefinovaná sada glyfů nastavená rozhraním IDE, jako je například visacího zámku nezobrazuje pro glyf "vrácených do", a zaškrtnutí jako glyf "rezervováno".  
  
### <a name="custom-set-of-glyphs"></a>Vlastní sada glyfů  
 VSPackage správy zdrojového kódu může při instalaci používat vlastní glyfy pro jedinečné "vzhled". Když je aktivní nový prvek VSPackage správy zdrojového kódu, měl by být schopný začít používat jeho vlastní glyfy i v případě, že je ještě načten předchozí ovládací prvek VSPackage zdrojového kódu, ale neaktivní. V tomto režimu může model VSPackage správy zdrojového kódu stále používat stávající ikony, aby bylo možné zachovat vzhled konzistentní s tím, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] že se rozhodne.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>Služba podporuje rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> které VSPackage může volitelně implementovat a které bude požádáno o rozhraní IDE. Když IDE vytvoří požadavek, pak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se znovu pokusí získat toto rozhraní z aktuálně registrovaného balíčku VSPackage pro správu zdrojového kódu. Pokud rozhraní existuje v registrované VSPackage, požadavek rozhraní IDE pro vlastní glyfy bude úspěšný. v opačném případě [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozhraní IDE použije svou výchozí sadu glyfů.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>Metoda je používána nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] k získání seznamu obrázků zobrazujících různé stavy správy zdrojů. Správa zdrojového kódu se vrátí do integrovaného vývojového prostředí (IDE) a popisovač do seznamu obrázků pro vlastní glyfy. Rozhraní IDE vytvoří v tomto okamžiku kopii seznamu obrázků a použije ji později k výběru glyfů, které se mají zobrazit. Pokud nové rozhraní není podporováno nebo `IVsSccGlyphs::GetCustomGlyphList` Metoda vrátí E_NOTIMPL, rozhraní IDE získá své glyfy z výchozího seznamu glyfů dodaných pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
