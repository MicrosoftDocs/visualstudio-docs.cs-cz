---
title: Starší verze rozhraní v editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5fdabadc1c3a0b5deda42aa268607e0f764e9b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849928"
---
# <a name="legacy-interfaces-in-the-editor"></a>Starší verze rozhraní v editoru
Editor sady Visual Studio můžete přistupovat ze starší verze rozhraní. Visual Studio SDK zahrnuje adaptérů, označované jako *překrytí*, která umožňují tato rozhraní pro interakci s nového editoru. Doporučujeme však, že aktualizujete starší kód Refaktorovat pro použití nového editoru rozhraní API. Váš kód budou líp fungovat a využívat nové technologie, jako je Windows Presentation Foundation (WPF) a Managed Extensibility Framework (MEF).  

## <a name="related-topics"></a>Související témata  

| Název | Popis |
| - | - |
| [Přizpůsobení staršího kódu do editoru](../extensibility/adapting-legacy-code-to-the-editor.md) | Vysvětluje, jak přizpůsobit kód do nového editoru. |
| [Nové nebo změněné chování editoru adaptéry](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | Vysvětluje, jak se liší od starších verzí editoru chování editoru adaptéry. |
| [V editoru core](../extensibility/inside-the-core-editor.md) | Popisuje různé součásti dřívějších verzích editoru. |
| [Vytvořit instanci editoru core pomocí starší verze rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | Vysvětluje způsob používání starší verze rozhraní API k vytvoření instance základní editor. |
| [Objekty pro vytváření editoru](../extensibility/editor-factories.md) | Vysvětluje, jak používat objekty pro vytváření editoru pomocí starší verze rozhraní API. |
| [Postupy: registrace editor typů souborů](../extensibility/how-to-register-editor-file-types.md) | Vysvětluje, jak propojit příponu názvu souboru do editoru. |
| [Návod: Vytvoření základní editor a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | Vysvětluje, jak vytvořit základní editor a odkaz na něj příponu názvu souboru. |
| [Postupy: zadání editory kontextu](../extensibility/how-to-provide-context-for-editors.md) | Vysvětluje, jak poskytnout kontext pro editor. |
| [Jazykové služby a základní editor](../extensibility/language-services-and-the-core-editor.md) | Vysvětluje interakce mezi služba jazyka a editoru. |
| [Přístup k vyrovnávací paměti textu pomocí starší verze rozhraní API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | Vysvětluje, jak získat přístup k vyrovnávací paměti textu pomocí starší verze rozhraní API. |
| [Zobrazit text přístup pomocí starší verze rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | Vysvětluje, jak získat přístup k zobrazení textu pomocí starší verze rozhraní API. |
| [Přizpůsobení windows kód pomocí starší verze rozhraní API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | Vysvětluje, jak přizpůsobit kód windows pomocí starší verze rozhraní API. |
| [Vrstvy přístupu k textu pomocí starší verze rozhraní API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | Vysvětluje, jak získat přístup k jiné vrstvy textu pomocí starší verze rozhraní API. |
| [Text značky pomocí starší verze rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md) | Vysvětluje, jak přidat text značky pomocí starší verze rozhraní API. |
| [Přizpůsobení nabídky a ovládací prvky editoru pomocí starší verze rozhraní API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | Vysvětluje, jak přizpůsobit ovládací prvky editoru pomocí starší verze rozhraní API. |
| [Správa vrácení zpět a znovu pomocí starší verze rozhraní API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | Vysvětluje, jak spravovat vrácení zpět a znovu pomocí starší verze rozhraní API. |
| [Postupy: implementace najít a nahradit mechanismus](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | Vysvětluje, jak spravovat najít a nahradit pomocí starší verze rozhraní API. |
| [Postupy: potlačení oznámení o změně souborů](../extensibility/how-to-suppress-file-change-notifications.md) | Vysvětluje, jak můžete potlačit oznámení o změně souborů pomocí starší verze rozhraní API. |
| [Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md) | Vysvětluje vytváření vlastních editorů a návrhářů. |
| [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md) | Obsahuje odkazy na dokumenty o funkcích, které umožňují přizpůsobení [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základním editoru tak, že přidáte podporu pro jazykové služby. |
| [Použití písem a barev](../extensibility/using-fonts-and-colors.md) | Vysvětluje, jak pomocí starší verze rozhraní písma a barvy. |

