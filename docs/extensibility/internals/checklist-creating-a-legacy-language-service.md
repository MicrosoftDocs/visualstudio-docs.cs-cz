---
title: 'Kontrolní seznam: vytvoření služby starší verze jazyka | Microsoft Docs'
description: Seznamte se se základními kroky, které musíte provést při vytváření služby starší verze jazyka pro základní editor sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 111e72714f4afd56b7b53e9cc48329ba6ce68162
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074792"
---
# <a name="checklist-create-a-legacy-language-service"></a>Kontrolní seznam: vytvoření služby starší verze jazyka
Následující kontrolní seznam shrnuje základní kroky, které je třeba provést, aby bylo možné vytvořit službu jazyka pro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] základní editor. Chcete-li integrovat službu jazyka do nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , je nutné vytvořit vyhodnocovací filtr výrazů ladění. Další informace naleznete v tématu [Write a vyhodnocovací filtr výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) v [rozšíření ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Postup vytvoření jazykové služby

1. Implementujte rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - Ve VSPackage implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní pro poskytování jazykové služby.

    - Zpřístupněte službu jazyka pro integrované vývojové prostředí (IDE) ve vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementaci.

2. Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní v hlavní třídě Language Service.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Rozhraní je počátečním bodem interakce mezi základním editorem a jazykovou službou.

### <a name="optional-features"></a>Volitelné funkce
 Následující funkce jsou volitelné a lze je implementovat v libovolném pořadí. Tyto funkce zvyšují funkčnost vaší jazykové služby.

- Barevné zvýrazňování syntaxe

  Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Vaše implementace tohoto rozhraní by měla vrátit informace o příslušné barvě z analyzátoru.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>Metoda vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní. Pro každou vyrovnávací paměť textu je vytvořena samostatná instance Colorizer, takže byste měli implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní samostatně. Další informace najdete v tématu [barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Okno kódu

  Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní, aby služba jazyka umožnila dostat oznámení o tom, kdy se vytvoří nové okno kódu.

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>Metoda vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní. Služba jazyka pak může přidat speciální uživatelské rozhraní do okna Code (kód) v nástroji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Služba jazyka může také provádět jakékoli speciální zpracování, jako je například přidání filtru zobrazení textu v nástroji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .

- Filtr zobrazení textu

  Chcete-li poskytnout dokončování příkazů IntelliSense v jazykové službě, je nutné zachytit některé příkazy, které by jinak zpracovával zobrazení textu. Chcete-li tyto příkazy zachytit, proveďte následující kroky:

  - Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pro účast v řetězení příkazů a zpracování příkazů editoru.

  - Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodu a předejte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementaci.

  - Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metodu při odpojení od zobrazení, aby se tyto příkazy již neprošly.

  Příkazy, které je třeba zpracovat, závisí na poskytovaných službách. Další informace najdete v tématu [Důležité příkazy pro filtry služby jazyka](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>Rozhraní musí být implementováno na stejném objektu jako <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní.

- Dokončování příkazů

  Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Podpora příkazu pro dokončení příkazu (tj. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) a volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní, předání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> rozhraní. Další informace najdete v tématu [dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Tipy k metodě

  Implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní, aby poskytovalo data pro okno s tipem pro metodu.

  Nainstalujte filtr zobrazení textu pro správné zpracování příkazů, abyste věděli, kdy zobrazit okno s tipem pro data metody. Další informace najdete v tématu [informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Chybové značky

  Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Vytvořte objekty značky chyby, které implementují <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní, a zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodu a předejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní objektu značky chyby.

  Každá značka chyby obvykle spravuje položku v okně seznam úkolů.

- Položky seznamu úkolů

  Implementujte třídu položky úkolu poskytující <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> rozhraní.

  Implementujte třídu poskytovatele úlohy, která poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> rozhraní.

  Implementujte třídu enumerátoru úlohy, která poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> rozhraní.

  Zaregistrujte poskytovatele úlohy pomocí metody seznamu úkolů <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .

  Získejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> rozhraní voláním poskytovatele služeb jazykové služby s identifikátorem GUID služby <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .

  Vytvořte objekty položky úkolu a zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> metodu v rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> když existují nové nebo aktualizované úkoly.

- Poznámky k položkám úkolu

  Použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> rozhraní k získání tokenů úlohy komentářů.

  Získejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> rozhraní ze <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> služby.

  Získejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> rozhraní z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metody.

  Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> rozhraní, aby naslouchalo změnám v seznamu tokenů.

- Sbalování

  K dispozici je několik možností pro podporu sbalení. Například můžete podporovat příkaz **sbalit na definice** , poskytnout oblasti pro sestavování s editorem, případně nastavit oblasti pro řízení klientů. Další informace najdete v tématu [Postup: poskytování rozšířené podpory sbalení ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Registrace služby jazyka

  Další informace o tom, jak zaregistrovat jazykovou službu, najdete v tématu [Registrace starší verze jazykové služby](../../extensibility/internals/registering-a-legacy-language-service2.md) a [Správa VSPackage](../../extensibility/managing-vspackages.md).

- Kontextově závislá Nápověda

  Poskytněte kontext editoru jedním z následujících způsobů:

  - Poskytněte kontext pro textové značky implementací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> rozhraní.

  - Poskytněte všechny uživatelské kontexty implementací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> rozhraní.

## <a name="see-also"></a>Viz také
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
