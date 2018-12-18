---
title: Otevření a uložení položky projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 895306a70d386b7a895b52b22704ec42a07d17ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130594"
---
# <a name="opening-and-saving-project-items"></a>Otevření a uložení položky projektu
Když přidáte nový typ projektu, musí spravovat otevírání a ukládání souborů projekty v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE). Následující témata popisují různé přístupy k otevření a uložení souborů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Zobrazení souborů pomocí příkazu Otevřít soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Poskytuje podrobné vysvětlení způsobu, jakým IDE zpracovává **otevření souboru** příkazu a roli projekty reagovat na tento příkaz.  
  
 [Zobrazení souborů pomocí příkazu Otevřít v aplikaci](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Poskytuje podrobné vysvětlení způsobu, jakým IDE zpracovává **otevřít v** příkazu výzvy otevírání souboru, který obsahuje některé volbu standardní editory.  
  
 [Postupy: Otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)  
 Poskytuje podrobné pokyny pro určení, že soubory určitého typu ve vašem projektu musí být otevřen v editoru specifické pro projekt.  
  
 [Postupy: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)  
 Poskytuje podrobné pokyny pro určíte, jak povolit IDE otevřete standardní editor pro soubory v typu vašeho projektu.  
  
 [Postupy: Otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Poskytuje podrobné pokyny k otevření editoru projektu specifické pro otevření souboru.  
  
 [Uložení standardního dokumentu](../../extensibility/internals/saving-a-standard-document.md)  
 Poskytuje podrobné vysvětlení, jak rozhraní IDE zpracovává **Uložit**, **uložit jako**, a **Uložit vše** příkazy pro dokument otevřít v standardního editoru.  
  
 [Uložení vlastního dokumentu](../../extensibility/internals/saving-a-custom-document.md)  
 Poskytuje podrobné vysvětlení způsobu, jakým zpracovává prostředí IDE a diagramu **Uložit**, **uložit jako**, a **Uložit vše** příkazy pro dokumenty otevřít v vlastní editor.  
  
 [Určení editoru, který otevře soubor v projektu](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Popisuje proces, který následuje integrovaného vývojového prostředí a vyberte příslušné editor nebo designer pro soubor.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytváření vlastních editorů a návrhářů](../../extensibility/creating-custom-editors-and-designers.md)  
 Uvádí čtyři typy editory, může hostovat rozhraní IDE a dává popisy jednotlivých editoru.  
  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Popisuje, jak projekty řízení způsobu, jakým je kód zkompilovat a vytvořené, jak jsou otevřené editory a způsob formátování položky projektu.