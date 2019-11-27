---
title: Upravit a pokračovat (vizuál C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef02f08ac635687eaaf071188ba0455c6389d9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301053"
---
# <a name="edit-and-continue-visual-c"></a>Upravit a pokračovat (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V vizuálních C++ projektech můžete použít možnost upravit a pokračovat. Informace o omezeních pro úpravu a pokračování naleznete v tématu [podporované změny kóduC++()](../debugger/supported-code-changes-cpp.md) .  
  
 Počínaje verzí Visual Studio 2015 Update 1 teď můžete v aplikacích pro Windows Store C++ a aplikacích rozhraní DirectX použít příkaz Upravit a pokračovat, protože teď podporuje přepínač **/Zi** Compiler s přepínačem **/bigobj** . V případě binárních souborů kompilovaných s přepínačem **/FastLink** můžete také použít možnost upravit a pokračovat.  
  
 Další vylepšení s aktualizací Update 1 zahrnují nové, zrušitelné dialogové okno a oznámení, když soubor nepodporuje operaci upravit a pokračovat. Další informace o vylepšeních aktualizace 1 najdete [v tématu vylepšení C++ úprav a pokračování v aktualizaci Visual Studio 2015 Update 1](https://devblogs.microsoft.com/cppblog/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1/).  
  
 Možnost kompilátoru [/Zo (rozšířené optimalizované ladění)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) , která byla představena ve službě Visual Studio 2013 Update 3, přidává další informace do souborů. pdb (symbol) pro binární soubory kompilované bez možnosti [/od (Disable (Ladit))](https://msdn.microsoft.com/library/aafb762y.aspx) .  
  
 **/Zo** zakáže funkci upravit a pokračovat. Viz [How to: Debug optimalizovaného kódu](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a>Povolit nebo zakázat úpravy a pokračovat  
 Pokud upravujete kód, který nechcete použít během aktuální relace ladění, je vhodné zakázat automatické vyvolání funkce upravit a pokračovat. Můžete také znovu povolit automatické úpravy a pokračovat.  
  
1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.  
  
2. V dialogovém okně **Možnosti** vyberte **ladění/obecné**.  
  
3. Ve skupině **Upravit a pokračovat** zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit nativní úpravu a pokračování** .  
  
   Změna tohoto nastavení ovlivní všechny projekty, na kterých pracujete. Po změně tohoto nastavení nemusíte aplikaci znovu sestavovat. Nastavení můžete změnit i při ladění. Při sestavování aplikace z příkazového řádku nebo ze souboru pravidel, ale ladění v prostředí Visual Studio, můžete i nadále používat možnost upravit a pokračovat, pokud nastavíte možnost **/Zi** .  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a>Explicitní použití změn kódu  
 V jazyce C++Visual mohou upravit a pokračovat použít změny kódu dvěma způsoby. Změny kódu lze použít implicitně, pokud vyberete příkaz pro spuštění nebo explicitně pomocí příkazu **použít změny kódu** .  
  
 Při explicitním použití změn kódu zůstane program v režimu pozastavení – nebude provedeno žádné spuštění.  
  
- Chcete-li použít změny kódu explicitně, v nabídce **ladění** vyberte možnost **použít změny kódu**.  
  
## <a name="BKMK_How_to_stop_code_changes"></a>Zastavení změn kódu  
 I když je proces úpravy a pokračování v procesu aplikování změn kódu, můžete operaci zastavit.  
  
 Zastavení použití změn kódu:  
  
- V nabídce **ladění** vyberte možnost **zastavit aplikování změn kódu**.  
  
  Tato položka nabídky je viditelná pouze v případě, že jsou aplikovány změny kódu.  
  
  Pokud zvolíte tuto možnost, není potvrzena žádná změna kódu.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a>Postup obnovení bodu provádění  
 Některé změny kódu můžou způsobit, že se bod spuštění přesune do nového umístění, když se změny upraví a pokračuje. Možnost upravit a pokračovat umístí místo spuštění co nejpřesněji, ale výsledky nemusí být ve všech případech správné.  
  
 V vizuálu C++se zobrazí dialogové okno, když se změní bod provádění. Před pokračováním v ladění je vhodné ověřit, zda je umístění správné. Pokud není správný, použijte příkaz **nastavit další příkaz** . Další informace najdete v tématu [nastavení dalšího příkazu ke spuštění](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a>Jak pracovat se zastaralým kódem  
 V některých případech nemůže příkaz Upravit a pokračovat ve spustitelném souboru okamžitě použít změny kódu, ale po pokračování v ladění může být možné použít změny kódu později. K tomu dojde, pokud upravíte funkci, která volá aktuální funkci, nebo pokud do funkce v zásobníku volání přidáte více než 64 bajtů nových proměnných.  
  
 V takových případech ladicí program pokračuje ve spouštění původního kódu, dokud se změny nedají použít. V samostatném okně zdrojového kódu se zobrazí zastaralý kód jako dočasné okno zdrojového souboru s názvem, jako je například `enc25.tmp`. Upravovaný zdroj se nadále zobrazuje v původním okně zdrojového kódu. Pokud se pokusíte upravit zastaralý kód, zobrazí se varovná zpráva.  
  
## <a name="see-also"></a>Viz také  
 [Podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md)
