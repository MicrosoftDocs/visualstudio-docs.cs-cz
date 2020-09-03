---
title: Poskytování kontextu jazykové služby pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193863"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Poskytnutí kontextu jazykové služby pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Existují dvě možnosti, jak služba jazyka poskytuje kontext uživatele pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základního editoru: Zadejte kontext značky textu nebo zadejte všechny uživatelské kontexty. Zde jsou uvedeny rozdíly mezi jednotlivými.  
  
 Další informace o poskytování kontextu pro službu jazyka, která je připojena ke svému vlastnímu editoru, naleznete v tématu [How to: Context for Editors](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Zadání kontextu značky textu do editoru  
 Chcete-li poskytnout kontext pro chyby kompilátoru, které jsou označeny textovými značkami v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základním editoru, implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> rozhraní. V tomto scénáři služba jazyka poskytuje kontext pouze v případě, že se ukazatel myši nachází na textové značce. To umožňuje, aby Editor poskytoval klíčové slovo na ukazateli do **dynamického okna Help** bez atributů.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Poskytněte všem uživatelským kontextům Editor.  
 Pokud vytváříte službu jazyka a používáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základní editor, můžete implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> rozhraní pro poskytování kontextu vaší jazykové služby.  
  
 Pro implementaci `IVsLanguageContextProvider` je k editoru připojen kontextový kontejner (kolekce), který je zodpovědný za aktualizaci balíčku kontextu. Když **dynamické okno Help** volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> rozhraní v tomto kontextu penalto v době nečinnosti, kontejner kontextu se dotazuje editoru pro aktualizaci. Editor potom upozorní službu jazyka, že by měl aktualizovat editor, a předá ukazatel na kontejner kontextu. To se provádí voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> metody z editoru do jazykové služby. Pomocí ukazatele na penalto kontextu může služba jazyka nyní přidávat a odebírat atributy a klíčová slova. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Existují dva různé způsoby, jak implementovat `IVsLanguageContextProvider` :  
  
- Poskytněte klíčové slovo pro kontejner kontextu.  
  
   Když je volán editor pro aktualizaci balíčku kontextu, předejte příslušná klíčová slova a atributy a pak vraťte `S_OK` . Tato návratová hodnota instruuje editor, aby zachoval klíčové slovo a kontext atributů namísto zadání klíčového slova na pozici kurzoru do balíčku kontextu.  
  
- Získat klíčové slovo z klíčového slova na pozici kurzoru  
  
   Když je volán editor pro aktualizaci balíčku kontextu, předejte příslušné atributy a pak vrátí `E_FAIL` . Tato návratová hodnota instruuje editor, aby zachoval vaše atributy v balíčku kontextu, ale aktualizovala kontextový balík pomocí klíčového slova na kurzoru.  
  
  Následující obrázek ukazuje, jak je k dispozici kontext pro službu jazyka, která implementuje `IVsLanguageContextProvider` .  
  
  ![Obrázek LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Kontext pro službu jazyka  
  
  Jak vidíte v diagramu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] má základní textový editor k němu připojen kontextový balík. Tento kontextový balík ukazuje na tři samostatné sáčky pro dílčí kontexty: službu jazyka, výchozí editor a značku textu. Jazykové služby a podkontexty značky textu obsahují atributy a klíčová slova pro službu jazyka, pokud <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> je rozhraní implementováno, a textové značky, pokud <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> je rozhraní implementováno. Pokud některá z těchto rozhraní neimplementujete, Editor poskytuje kontext pro klíčové slovo na pozici kurzoru ve výchozím vakuu podkontextu editoru.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Kontextové pokyny pro editory a návrháře  
 Návrháři a editory musí poskytovat klíčové slovo General pro Editor nebo okno návrháře. K tomu je potřeba, aby se pro návrháře nebo editor zobrazilo obecné, ale vhodné téma nápovědy, když uživatel stiskne klávesu F1. Editor musí kromě toho zadávat klíčové slovo na pozici kurzoru nebo zadávat klíčové termíny na základě aktuálního výběru. K tomu je potřeba zajistit, aby se téma nápovědy pro text nebo prvek uživatelského rozhraní, které se zobrazilo nebo vybrali, zobrazilo v okamžiku, kdy uživatel stiskne klávesu F1. Návrhář poskytuje kontext pro položku vybranou v návrháři, jako je například tlačítko na formuláři. Editory a návrháři se musí také připojit ke službě jazyka, jak je uvedeno v [základní verzi služby pro starší jazyky](../extensibility/internals/legacy-language-service-essentials.md).
