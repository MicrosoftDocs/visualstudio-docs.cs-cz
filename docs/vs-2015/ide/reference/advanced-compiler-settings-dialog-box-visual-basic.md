---
title: Pokročilé dialogové okno nastavení kompilátoru (Visual Basic) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd910b0e0295ca12807b96af189032ffec766429
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949822"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **AdvancedCompiler nastavení** dialogovému oknu **Návrháře projektu** k určení rozšířenou vlastností konfigurace sestavení projektu. Toto dialogové okno se vztahují na projekty Visual Basic pouze.  
  
### <a name="to-access-this-dialog-box"></a>Pro přístup k tomuto dialogovému oknu  
  
1. V **Průzkumníka řešení**, zvolte uzel projektu (ne **řešení** uzlu).  
  
2. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **Návrhář projektu** se zobrazí, klikněte na tlačítko **kompilace** kartu.  
  
3. Na [stránka kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), vyberte **konfigurace** a **platformy**. Ve zjednodušených konfigurací sestavení **konfigurace** a **platformy** seznamy se nezobrazují. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
4. Klikněte na tlačítko **Upřesnit možnosti kompilace**.  
  
   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="optimizations"></a>Optimalizace  
 Určete následující možnosti optimalizace, které můžete v některých případech zmenšit soubor programu, programu pracovat rychleji a urychlit proces sestavení.  
  
 **Odebrat kontroly přetečení celých čísel**  
 Ve výchozím nastavení je toto políčko zaškrtnuté povolíte kontrolu přetečení celého čísla. Zaškrtněte toto políčko, chcete-li odebrat kontroly přetečení celého čísla. Pokud toto políčko zaškrtnete, může být rychlejší výpočty celé číslo. Pokud odeberete přetečení kontrolu a datový typ kapacity přetečení, nesprávné výsledky může ukládat bez vyvolání chyby.  
  
 Pokud přetečení podmínky jsou kontrolovány a přetečení celočíselné operace <xref:System.OverflowException> je vyvolána výjimka. V případě přetečení podmínky nejsou zaškrtnuté, operace přetečení celého čísla nejsou vyvolává výjimku.  
  
 **Povolit optimalizace**  
 Ve výchozím nastavení je toto políčko zaškrtnuté zakázat optimalizace kompilátoru. Výběr tohoto políčka povolíte optimalizace kompilátoru. Optimalizace kompilátoru zkontrolujte výstupní soubor menší, rychlejší a efektivnější. Nicméně protože optimalizace způsobit změnou kódu do výstupního souboru, optimalizace kompilátoru mohou ztížit ladění.  
  
 **Základní adresa knihovny DLL**  
 Toto textové pole se zobrazí výchozí základní adresa knihovny DLL v šestnáctkovém formátu. V projektech knihovny tříd a Knihovna ovládacích prvků vám pomůže tohoto textového pole zadejte základní adresu, která se dá použít při vytvoření knihovny DLL.  
  
 **Generovat ladicí informace**  
 Vyberte **žádný**, **úplné**, nebo **pouze soubor pdb** ze seznamu. **Žádný** Určuje, že nebudou generována žádná informace o ladění. **Úplné** Určuje, že nebudou generována úplné ladicí informace, a **pouze soubor pdb** Určuje, že nebudou generována pouze soubor PDB ladicí informace. Ve výchozím nastavení je tato možnost nastavená na **úplné**.  
  
## <a name="compilation-constants"></a>Kompilace konstanty  
 Konstanty pro podmíněnou kompilaci mít podobný pomocí vliv [#Const](http://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) direktivy preprocesoru ve zdroji souborů, s tím rozdílem, že konstanty definované jsou veřejné a použít na všechny soubory v projektu. Můžete použít konstanty pro podmíněnou kompilaci spolu s [#If... Pak... #Else](http://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) direktivy podmíněné kompilace zdrojové soubory. Zobrazit [podmíněné kompilace](http://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).  
  
 **Definovat konstantu DEBUG**  
 Ve výchozím nastavení je toto políčko zaškrtnuto, určení nastavit konstantu DEBUG.  
  
 **Definovat konstantu TRACE**  
 Ve výchozím nastavení je toto políčko zaškrtnuto, určení nastavit konstantu TRACE.  
  
 **Vlastní konstanty**  
 Zadejte všechny vlastní konstanty pro vaši aplikaci do tohoto textového pole. Položky by měly být odděleny čárkami, pomocí tohoto formuláře: **Name1 = "Hodnota1", NAZEV2 = "Hodnota2", nazev3 = "Hodnota3"**.  
  
## <a name="other-settings"></a>Další nastavení  
 **Generování sestavení serializace**  
 Toto nastavení určuje, zda kompilátor vytvoří sestavení serializace XML. Sestavení serializace mohou zvýšit výkon při spuštění <xref:System.Xml.Serialization.XmlSerializer> Pokud jste již použili k serializaci typů ve vašem kódu. Ve výchozím nastavení je tato možnost nastavená na **automaticky**, která určuje, že se serializace sestavení vytvoří pouze v případě, že jste už použili <xref:System.Xml.Serialization.XmlSerializer> ke kódování typů ve vašem kódu pro XML. **Vypnout** Určuje, že sestavení serializace nebudou nikdy generována, bez ohledu na to, jestli váš kód používá <xref:System.Xml.Serialization.XmlSerializer>. **Na** Určuje, že sestavení serializace budou vždy generována. Jsou pojmenované sestavení serializace `TypeName`. XmlSerializers.dll.  
  
## <a name="see-also"></a>Viz také  
 [Stránka Kompilovat, Návrhář projektu (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)



