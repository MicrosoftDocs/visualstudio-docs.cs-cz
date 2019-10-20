---
title: 'Upozornění: &#39;soubor&#39; závislosti &#39;v projektu projektu&#39; nelze zkopírovat do běhového adresáře, protože by přepsal referenční &#39;soubor. &#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a619168bd07fde5d27e5c3d87dc46f505cf5268d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672823"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Upozornění: &#39;soubor&#39; závislosti &#39;v projektu projektu&#39; nelze zkopírovat do běhového adresáře, protože by přepsal referenční &#39;soubor.&#39;
Došlo ke konfliktu mezi závislostmi. do adresáře bin by se měla zkopírovat více než jeden samostatný soubor sestavení se stejným názvem, aby bylo možné aplikaci spustit. Spuštění adresáře dokáže vyřešit konflikt, protože jedna z závislostí je primární odkaz.

 Dvojím kliknutím na tuto položku Seznam úkolů přejdete na primární uzel odkazu, který je v konfliktu.

 K tomuto upozornění dochází, když dojde ke konfliktu závislosti, ale kolem něj jste přidali jednu z konfliktních závislostí jako referenci. Nebo jste mohli mít odkaz na verzi 1 a pak jste přidali druhý odkaz, který sám odkazuje na verzi 2 prvního odkazu.

 To znamená, že k této chybě dochází, protože projekty ve vašem řešení mají odkazy na sebe navzájem, ale odkazy byly vytvořeny jako odkazy na soubory (pomocí tlačítka **Procházet** v dialogovém okně [Přidat odkaz](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) ), nikoli z projektu do projektu. odkazy (pomocí karty **projekt** v dialogovém okně **Přidat odkaz** ). Výhodou odkazu na projekt je, že vytváří závislost mezi projekty v systému sestavení, takže závislý projekt bude sestaven, pokud se od posledního vytvoření odkazujícího projektu změnil. Odkaz na soubor nevytváří závislost sestavení, takže je možné sestavit odkazující projekt bez sestavení závislého projektu a odkaz může být zastaralý; projekt může odkazovat na dříve sestavenou verzi projektu. To může mít za následek, že v adresáři bin je vyžadováno několik verzí jediné knihovny DLL, což není možné a je výsledkem tato chybová zpráva.

 Tato zpráva se zobrazí při každém konfliktu v adresáři bin a aplikace nemusí správně fungovat. I když jste tento problém mohli vyřešit, toto upozornění se pořád zobrazí, protože systém projektu nemůže určit, jestli verze závislosti bude správně fungovat se všemi komponentami.

 **Oprava této chyby**

- Zkopírujte jeden (nebo nula) soubory sestavení do adresáře bin, které lze provést vložením souborů sestavení do globální mezipaměti sestavení (GAC). Globální mezipaměť sestavení řeší konflikty názvů souborů. Nebudou provedeny žádné místní kopie souboru sestavení, protože modul CLR (Common Language Runtime) ví, jak najít sestavení v globální mezipaměti sestavení (GAC). Další informace naleznete v tématu [práce se sestaveními a globální mezipamětí sestavení](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) a [Chyba: závislost ' file ' v projektu ' Project ' nelze zkopírovat do běhového adresáře, protože by byla v konfliktu se závislostí ' file '](/visualstudio/misc/error-dependency-file?view=vs-2015).

## <a name="see-also"></a>Viz také
 [Správa odkazů v](../ide/managing-references-in-a-project.md) [globální mezipaměti sestavení](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) v projektu [Postupy: vytvoření a odebrání závislostí projektu](../ide/how-to-create-and-remove-project-dependencies.md)