---
title: 'Postupy: aktualizace stavového řádku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703149"
---
# <a name="how-to-update-the-status-bar"></a>Postupy: Aktualizace stavového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Stavový řádek** je ovládací panel umístěný v dolní části řady oken aplikace, která obsahuje jeden nebo více stavových řádků nebo indikátorů.  
  
### <a name="to-update-the-status-bar"></a>Aktualizace stavového řádku  
  
1. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> na každý jednotlivý objekt zobrazení (objekt DocView), který poskytuje editor, jako je například zobrazení formuláře a zobrazení kódu.  
  
2. Při volání rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> aktualizujte informace ve **stavovém řádku** voláním metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > Rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> pouze při počáteční aktivaci okna dokumentu. Po zbytek času, kdy je okno dokumentu aktivní, je nutné aktualizovat informace o **stavovém řádku** jako stav změn editoru.  
  
## <a name="robust-programming"></a>Robustní programování  
 **Stavový řádek** obsahuje čtyři samostatná pole:  
  
- Stavový text  
  
- Indikátor průběhu  
  
- Animovaná ikona  
  
- Informace editoru  
  
  Další informace najdete v tématu [stavové řádky](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  Rozhraní IDE automaticky volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementace při aktivaci okna dokumentu.  
  
  Implementátor balíčku VSPackage zodpovídá za aktualizaci textu stavu ve stavovém řádku. Rozhraní IDE obnoví tento řetězec na "PŘIPRAVENo", pokud je textové pole stav nastaveno na prázdný text ("") v době nečinnosti.  
  
## <a name="see-also"></a>Viz také  
 [Stavové řádky](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
