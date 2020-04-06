---
title: 'Kontrolní seznam: Vytvoření služby staršího jazyka | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709794"
---
# <a name="checklist-create-a-legacy-language-service"></a>Kontrolní seznam: Vytvoření služby starších jazyků
Následující kontrolní seznam shrnuje základní kroky, které je třeba [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] provést, abyste vytvořili jazykovou službu pro základní editor. Chcete-li integrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]službu jazyka do aplikace , je nutné vytvořit vyhodnocení ladicího výrazu. Další informace naleznete [v tématu Write a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) in the [Visual Studio ladicí program rozšiřitelnost](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Postup vytvoření jazykové služby

1. Implementujte rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - Ve vašem VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementovat rozhraní poskytovat jazykovou službu.

    - Zpřístupněte svou jazykovou službu integrovanému vývojovému prostředí (IDE) v implementaci. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>

2. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní v hlavní třídě služby jazyka.

     Rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> je výchozím bodem interakce mezi editorem jádra a jazykovou službou.

### <a name="optional-features"></a>Volitelné funkce
 Následující funkce jsou volitelné a mohou být implementovány v libovolném pořadí. Tyto funkce zvyšují funkčnost jazykové služby.

- Zbarvení syntaxe

  Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Implementace tohoto rozhraní by měl analyzátor informace vrátit příslušné informace o barvě.

  Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní. Pro každou textovou vyrovnávací paměť je vytvořena samostatná <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> instance colorizeru, takže byste měli implementovat rozhraní samostatně. Další informace naleznete [v tématu Syntax coloring in a legacy language service](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Okno Kód

  Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní, které umožní službě jazyka přijímat oznámení o vytvoření nového okna kódu.

  Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní. Služba jazyka pak můžete přidat speciální uI <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>do okna kódu v . Služba jazyka může také provést jakékoli zvláštní zpracování, například přidání filtru zobrazení textu do . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>

- Filtr zobrazení textu

  Chcete-li poskytnout dokončování příkazu IntelliSense ve službě jazyka, musíte zachytit některé příkazy, které by jinak textové zobrazení zpracovat. Chcete-li tyto příkazy zachytit, proveďte následující kroky:

  - Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> k účasti v řetězci příkazů a popisovač editoru příkazy.

  - Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody a předat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> v implementaci.

  - Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metody při odpojení od zobrazení tak, aby tyto příkazy již nejsou předány k vám.

  Příkazy, které musí být zpracovány závisí na služby, které jsou k dispozici. Další informace naleznete v [tématu Důležité příkazy pro filtry jazykových služeb](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > Rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> musí být implementováno na <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> stejném objektu jako rozhraní.

- Dokončení výkazu

  Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Podporujte příkaz dokončení příkazu <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>(to <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> znamená ) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a volejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> metodu v rozhraní a předejte rozhraní. Další informace naleznete [v tématu Dokončení výkazu ve starší jazykové službě](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Tipy pro metody

  Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní poskytnout data pro okno tip metody.

  Nainstalujte filtr zobrazení textu pro vhodné zpracování příkazů, abyste věděli, kdy se má zobrazit okno tipu dat metody. Další informace naleznete [v tématu Informace o parametrech ve starší jazykové službě](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Značky chyb

  Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Vytvořte objekty značky <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> chyb, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> které implementují rozhraní a volají metodu a předávají <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní objektu značky chyby.

  Každá značka chyb obvykle spravuje položku v okně seznamu úkolů.

- Položky seznamu úkolů

  Implementujte třídu položky úkolu poskytující <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> rozhraní.

  Implementujte třídu zprostředkovatele úloh, která <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> poskytuje rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> rozhraní.

  Implementujte třídu výčtu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> úloh, která poskytuje rozhraní.

  Zaregistrujte poskytovatele úloh <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> metodou seznamu úkolů.

  Získejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> rozhraní voláním poskytovatele služeb jazykové služby <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>pomocí identifikátoru GUID služby .

  Vytvořte objekty položky úkolu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> a zavolejte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> v rozhraní, když jsou nové nebo aktualizované úkoly.

- Komentovat položky úkolu

  Pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> rozhraní získat tokeny úlohy komentáře.

  Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> rozhraní ze <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> služby.

  Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> rozhraní z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metody.

  Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> rozhraní naslouchat změnám v seznamu tokenů.

- Sbalování

  Existuje několik možností, jak podpořit osnovu. Můžete například podporovat příkaz **Sbalit do definic,** poskytnout oblasti osnovy řízené editorem nebo podporovat oblasti řízené klientem. Další informace naleznete v [tématu Postup: Poskytování rozšířené podpory ve službě starších jazyků](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Registrace jazykové služby

  Další informace o registraci jazykové služby naleznete v [tématu Registrace služby starších jazyků](../../extensibility/internals/registering-a-legacy-language-service2.md) a [Správa balíčků VSPackages](../../extensibility/managing-vspackages.md).

- Kontextová nápověda

  Poskytněte editoru kontext jedním z následujících způsobů:

  - Zadejte kontext pro textové značky implementací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> rozhraní.

  - Zadejte veškerý kontext uživatele <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> implementací rozhraní.

## <a name="see-also"></a>Viz také
- [Vývoj služby starších jazyků](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Napsat vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
