---
title: Příkaz okno | Dokumentace Microsoftu
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
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b83a9e86aea02e27242a0c1f02ca3f8459152214
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870182"
---
# <a name="command-window"></a>Příkazové okno
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Příkaz** okno se používá ke spuštění příkazů nebo přímo v aliasy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Můžete spustit příkazy nabídek a příkazů, které nejsou zobrazeny na jakékoliv nabídky. Pro zobrazení **příkaz** okně zvolte **ostatní Windows** z **zobrazení** nabídky a vybereme **příkazové okno**.  
  
## <a name="displaying-the-values-of-variables"></a>Zobrazení hodnot proměnných  
 Chcete-li zkontrolovat hodnotu proměnné `varA`, použijte [příkaz Tisk](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Otazník (?) je alias pro `Debug.Print`, takže tento příkaz lze také zapsat:  
  
```  
>? varA  
```  
  
 Obě verze tohoto příkazu vrátí hodnotu proměnné `varA`.  
  
## <a name="entering-commands"></a>Zadávání příkazů  
 Větší než symbol (`>`) se zobrazí na levém okraji příkazové okno příkazovém řádku pro nové řádky. Pomocí kláves Šipka nahoru a Šipka dolů procházejte dříve vydané příkazy.  
  
|Úloha|Řešení|Příklad|  
|----------|--------------|-------------|  
|Vyhodnocení výrazu.|Výraz začíná otazníkem otazníkem (`?`).|`? myvar`|  
|Přepnout na příkazovém podokně.|Zadejte `immed` do okna bez znak větší než (>)|`immed`|  
|Přepněte zpět do příkazového okna v příkazovém podokně.|Zadejte `cmd` do okna.|`>cmd`|  
  
 Následující klávesové zkratky umožňují přejděte v příkazovém režimu.  
  
|Akce|Umístění kurzoru|Klávesové zkratky|  
|------------|---------------------|----------------|  
|Cyklicky procházet seznam dříve zadaných příkazů.|Vstupním řádku|ŠIPKA &AMP; DOLŮ ŠIPKA NAHORU|  
|Posunout okno.|Obsah příkazového okna|CTRL + ŠIPKA NAHORU|  
|Posuňte se dolů v okně.|Obsah příkazového okna|Šipka dolů nebo CTRL + ŠIPKA DOLŮ|  
  
> [!TIP]
>  Část nebo celý předchozího příkazu můžete zkopírovat na vstupním řádku posouvání, aby ji mohl, zvýraznění nebo jeho část a pak stisknutím klávesy ENTER.  
  
## <a name="mark-mode"></a>Režim označení  
 Po kliknutí na libovolný předchozí řádek v **příkaz** okna, posunete automaticky do režimu označení. To vám umožňuje vybrat, upravit a zkopírujte text z předchozích příkazů, jako by v libovolném textovém editoru a vložte je do aktuálního řádku.  
  
## <a name="the-equals--sign"></a>Znaménko rovná se (=)  
 V okně použité ke vstupu `EvaluateStatement` příkaz určuje, zda je znak rovná se (=) interpretován jako porovnávací operátor nebo jako operátor přiřazení.  
  
 V **příkaz** okně znak rovná se (=) interpretován jako operátor porovnání. Operátory přiřazení v nelze použít **příkaz** okna. Tak například, pokud hodnoty proměnných `varA` a `varB` jsou odlišné, pak příkaz  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 Vrátí hodnotu `False`.  
  
 V **okamžité** okna, naopak znak rovná se (=) interpretován jako operátor přiřazení. Ano například příkaz  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 přiřadí proměnné `varA` hodnotu proměnné `varB`.  
  
## <a name="parameters-switches-and-values"></a>Parametry, přepínače a hodnoty  
 Některé [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vyžadovala trojnásobnou investici příkazy přepínače a hodnot a volitelné argumenty. Některá pravidla platí při zpracování komplexnějších pomocí těchto příkazů. Následuje příklad bohaté příkazu vyjasnit terminologii.  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 V tomto příkladu  
  
- `Edit.ReplaceInFiles` příkaz  
  
- `/case` a `/pattern:regex` přepínače (začíná znakem lomítka [/])  
  
- `regex` je hodnota `/pattern` přepnout; `/case` přepínač nemá žádnou hodnotu.  
  
- `var[1-3]+` a `oldpar` jsou parametry  
  
  > [!NOTE]
  >  Příkaz, parametrů, přepínače nebo hodnotu, která obsahuje mezery, musí mít dvojitých uvozovek na obou stranách.  
  
  Pozice přepínače a parametry jsou navzájem zaměnitelné volně na příkazovém řádku s výjimkou produktů [prostředí](../../ide/reference/shell-command.md) příkaz, který vyžaduje svou přepínače a parametry v určitém pořadí.  
  
  Téměř každý přepínač podporuje příkaz má dvě různými formami: krátká forma (jeden znak) a dlouhém formátu. Více přepínačů krátkometrážní zkombinovat do skupiny. Například `/p /g /m` lze také vyjádřit jako `/pgm`.  
  
  Pokud krátkometrážní přepínače jsou sloučeny do skupiny a přidělenou hodnotu, tato hodnota se vztahuje na každý přepínač. Například `/pgm:123` odpovídá `/p:123 /g:123 /m:123`. Pokud některý z přepínačů ve skupině nepřijímá hodnotu, dojde k chybě.  
  
## <a name="escape-characters"></a>Řídicí znaky  
 Znak stříšky (^) v příkazovém řádku znamená, že znak, který bezprostředně následují je interpretován doslovně a ne jako řídicí znak. To slouží k vložení uvozovek ("), mezer, úvodních lomítek, střížek nebo jakýmikoli literálními znaky parametru nebo hodnotě switch s výjimkou názvů switchů. Například  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Stříška funguje stejně, ať už se jedná o vnitřní nebo vnější uvozovky. Pokud poslední znak na řádku stříška, je ignorován. Z příkladu ukazuje, jak vyhledat vzor "^ t".  
  
## <a name="use-quotes-for-path-names-with-spaces"></a>Nabídky použijte pro názvy cesty obsahující mezery  
 Pokud například chcete otevřít soubor, který obsahuje cestu obsahující mezery, je nutné umístit dvojité uvozovky kolem cestu nebo segment cesty, který obsahuje mezery: **C:\\"Program Files"** nebo **"C:\Program Files"**.  
  
## <a name="see-also"></a>Viz také  
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)



