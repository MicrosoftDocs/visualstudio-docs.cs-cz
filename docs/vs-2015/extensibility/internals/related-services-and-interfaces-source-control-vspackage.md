---
title: Související služby a rozhraní (VSPackage správy zdrojového kódu) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c5b040a8c5d0cbe2daff07f279cfd6a78cbd2b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157395"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Související služby a rozhraní (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V této části jsou uvedena všechna rozhraní týkající se správy zdrojového kódu, která jsou součástí sady VSPackage [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] . Rozhraní VSPackage správy zdrojového kódu implementuje některá z těchto rozhraní a používá jiné k provádění úloh správy zdrojového kódu.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Rozhraní implementovaná pomocí a pro VSPackage správy zdrojového kódu  
 Následující rozhraní jsou popsána v tématu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] a sada VSPackage správy zdrojového kódu implementuje podmnožinu těchto rozhraní v závislosti na požadované sadě funkcí. Některá rozhraní jsou označena jako povinná a musí být implementovaná všemi všemi prvky VSPackage správy zdrojového kódu.  
  
 Pro taková rozhraní, která balíček neimplementuje, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje výchozí implementaci. Všimněte si, že výchozí implementace je navržena pro případ, kdy není zaregistrován žádný VSPackage a není kontrolován žádný projekt. Správně napsaný ovládací prvek VSPackage implementuje všechna nezbytná rozhraní a neopouští ho výchozí implementací těchto rozhraní.  
  
 VSPackage správy zdrojového kódu musí implementovat privátní službu, která zapouzdřuje některá nebo všechna následující rozhraní.  
  
 Rozhraní jsou:  
  
- Požadováno: příslušné entity (správy zdrojového kódu, zástupné procedury správy zdrojového kódu, projektu) musí implementovat rozhraní.  
  
- Doporučené: entita by měla implementovat toto rozhraní; v opačném případě můžou být funkce správy zdrojového kódu omezené.  
  
- Volitelné: entita může implementovat toto rozhraní, aby poskytovala bohatou sadu funkcí.  
  
|Rozhraní|Účel|Implementuje|Uskutečnit?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editory volají toto rozhraní před úpravou nebo uložením souboru. Prvek VSPackage správy zdrojového kódu může soubor rezervovat nebo zamítnout operaci, pokud se registrace nepovede.|VSPackage správy zdrojového kódu|Doporučeno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Toto rozhraní poskytuje základní funkce správy zdrojového kódu pro projekty, jako je registrace a zrušení registrace projektů se správou zdrojových kódů a poskytování podpory pro základní piktogramy správy zdrojového kódu.|VSPackage správy zdrojového kódu|Vyžadováno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Toto rozhraní se získává z rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> pomocí <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> funkce nebo pouhým přetypováním objektu, `IVsHierarchy` který implementuje na `IVsSccProject2` . Slouží k získávání souborů pod správou zdrojových kódů v projektu nebo pro informování projektu aktuálního stavu nebo umístění správy zdrojových kódů.|Project|Vyžadováno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Modul Integration Module používá toto rozhraní k nastavení aktuálního aktivního balíčku VSPackage.|VSPackage správy zdrojového kódu|Vyžadováno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Toto rozhraní je založené na modelu předplatného. Libovolný VSPackage může signalizovat, že chce přijímat události dokumentu a že prostředí doporučuje pro události, ke kterým dochází. Je implementován a zpracováván pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , který zase předává události, které implementují rozhraní `IVsTrackProjectDocumentsEvents2` VSPackage.|Zástupný kód správy zdrojového kódu|Vyžadováno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Toto rozhraní poskytuje dávkové zpracování, synchronizovanou operace čtení a zápisu a pokročilou `OnQueryAddFiles` metodu.|Zástupný kód správy zdrojového kódu|Vyžadováno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Průzkumník řešení** a projekty volají toto rozhraní, když jsou do projektů přidány nové soubory, nebo když jsou soubory a složky přejmenovány nebo odstraněny z projektů. Prvek VSPackage správy zdrojového kódu může rezervovat soubor projektu nebo operaci zrušit.|VSPackage správy zdrojového kódu|Doporučeno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Průzkumník řešení** a projekty volají toto rozhraní v reakci na volání metod rozhraní IVstrackProjectDocuments3. VSPackage správy zdrojového kódu může sledovat dávkové operace, synchronizované operace čtení a zápisu a pracovat s pokročilejší `OnQueryAddFiles` metodou.|VSPackage správy zdrojového kódu|Doporučeno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Toto rozhraní poskytuje podporu správy zařazení pro webové projekty.|VSPackage správy zdrojového kódu|Doporučeno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Toto rozhraní se používá k načtení popisů tlačítek pro soubory se spravovanými zdroji v projektech.|VSPackage správy zdrojového kódu|Volitelné|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Toto rozhraní poskytuje podporu rozšíření oboru názvů.|VSPackage správy zdrojového kódu|Volitelné|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage používá toto rozhraní k integraci rozšíření oboru názvů do dialogových oken **Nová**, **otevřít**nebo **Uložit** . V důsledku toho mohou být projekty automaticky přidány do správy zdrojového kódu při vytváření nebo přidány do správy zdrojového kódu, když je platná operace uložení.|VSPackage správy zdrojového kódu|Volitelné|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage používá toto rozhraní k definování dalších glyfů jako glyfy správy zdrojového kódu pro uzly v **Průzkumník řešení**.|VSPackage správy zdrojového kódu|Volitelné|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|Toto rozhraní používá dialogové okno **Přidat** pro webové projekty. Poskytuje metody pro procházení umístění správy zdrojových kódů a pro otevření webového projektu, který byl dříve přidán do úložiště správy zdrojového kódu v tomto umístění.|VSPackage správy zdrojového kódu|Doporučeno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Toto rozhraní poskytuje podporu pro asynchronní (Background) načítání projektů ze správy zdrojového kódu.|VSPackage správy zdrojového kódu|Volitelné|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Toto rozhraní umožňuje projektům sledovat průběh asynchronního načítání iniciované <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> .|Project|Volitelné|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Toto rozhraní umožňuje integrovanému vývojovém prostředí (IDE) dotazovat se na aktivní správu zdrojového kódu. Rozhraní IDE se dotazuje na hodnotu nastavení správy zdrojového kódu, která má význam i v případě, že není zaregistrována žádná aktivní správa zdrojového kódu. Toto rozhraní je implementováno a zpracováno nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .|Zástupný kód správy zdrojového kódu|Vyžadováno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Toto rozhraní se používá při registraci balíčku VSPackage správy zdrojového kódu.|Zástupný kód správy zdrojového kódu|Vyžadováno|  
|<xref:EnvDTE.SourceControl>|Toto rozhraní se používá v automatizaci. V takovém případě zpřístupňuje pouze funkce, které lze provést bez zobrazení uživatelského rozhraní.|VSPackage správy zdrojového kódu|Volitelné|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Toto rozhraní slouží k uložení nastavení správy zdrojů do souboru řešení (. sln). Mezi tato nastavení patří umístění správy zdrojových kódů a příznaky stavu správy zdrojového kódu.|VSPackage správy zdrojového kódu|Doporučeno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Toto rozhraní slouží k uložení nastavení správy zdrojů v souboru možností řešení (. suo). To může zahrnovat nastavení správy zdrojového kódu specifická pro uživatele, jako je například umístění zařazení aktuálního uživatele.|VSPackage správy zdrojového kódu|Doporučeno|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Toto rozhraní slouží k monitorování událostí za účelem provedení operací, jako je vrácení souborů projektu před zavřením řešení nebo získání nových souborů ze správy zdrojového kódu při otevření projektu.|VSPackage správy zdrojového kódu|Doporučeno|  
  
## <a name="see-also"></a>Viz také  
 [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
