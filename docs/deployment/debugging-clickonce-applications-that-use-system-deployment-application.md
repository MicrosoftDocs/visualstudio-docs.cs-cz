---
title: Ladění aplikací ClickOnce používajících System.Deployment.Application | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c877c3373f7d028291b521558a04fafd56e022c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836356"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Ladění aplikací ClickOnce používajících System.Deployment.Application
V [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení můžete konfigurovat, jak se aplikace aktualizuje. Nicméně, pokud je potřeba použít a přizpůsobit advanced [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] potřebuje pro funkce nasazení, musíte pro přístup k modelu objektu nasazení poskytované <xref:System.Deployment.Application>. Můžete použít <xref:System.Deployment.Application> rozhraní API pro pokročilé úlohy jako například:  
  
- Vytváření možnost "Aktualizace nyní" v aplikaci  
  
- Podmíněné, ke stažení na vyžádání z různých částí aplikace  
  
- Aktualizace, které jsou integrované přímo do aplikace  
  
- Zajištění, že klientská aplikace bude pořád aktuální  
  
  Vzhledem k tomu, <xref:System.Deployment.Application> rozhraní API pracovat pouze, když je aplikace nasazená s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologií, jediným způsobem, jak ladit je k nasazení aplikace pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], připojit se k němu a pak ho ladit. Může být obtížné připojit ladicí program dostatečně včas, protože tento kód často se spustí při spuštění aplikace a spustí, než budete moct připojit ladicí program. Řešení je umístit před aktualizace zkontrolujte kód nebo kód na vyžádání přerušení (nebo zastavení pro projekty jazyka Visual Basic).  
  
  Ladění doporučený postup je následující:  
  
1. Než začnete, ujistěte se, že symbolu (.pdb) a zdrojové soubory jsou archivovány.  
  
2. Nasazení aplikace verze 1.  
  
3. Vytvoření nové prázdné řešení. Z **souboru** nabídky, klikněte na tlačítko **nový**, pak **projektu**. V **nový projekt** dialogovém okně Otevřít **ostatní typy projektů** uzlu, vyberte **řešení sady Visual Studio** složky. V **šablony** vyberte **prázdné řešení**.  
  
4. Přidáte umístění archivované zdroje do vlastnosti pro toto nové řešení. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení a pak klikněte na tlačítko **vlastnosti**. V **stránky vlastností** dialogu **zdrojové soubory ladění**, pak přidejte adresář archivované zdrojového kódu. V opačném případě ladicí program najdete zastaralé zdrojové soubory, protože zdrojové cesty k souborům se zaznamenávají do souboru pdb. Pokud ladicí program používá zastaralý zdrojové soubory, zobrazí se zpráva, která neodpovídá zdroji.  
  
5. Ujistěte se, že ladicí program můžete najít *PDB* soubory. Pokud jste nasadili je s vaší aplikací, ladicí program nalezne je automaticky. Vždy vypadá vedle sestavení dotyčný nejprve. V opačném případě budete muset přidat cestu k archivu do **Symbol umístění souborů (.pdb)** (pro přístup k této možnosti z **nástroje** nabídky, klikněte na tlačítko **možnosti**, otevřete  **Ladění** uzel a klikněte na tlačítko **symboly**).  
  
6. Ladění, co se stane, že mezi `CheckForUpdate` a `Download` / `Update` volání metody.  
  
    Aktualizace kódu může být například následujícím způsobem:  
  
   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Nasazení verze 2.  
  
8. Pokus připojit ladicí modul k aplikace verze 1, protože stahuje aktualizace pro verzi 2. Případně můžete použít `System.Diagnostics.Debugger.Break` metoda nebo jednoduše `Stop` v jazyce Visual Basic. Samozřejmě by neměl nechat volání těchto metod v produkčním kódu.  
  
    Předpokládejme například, vyvíjíte aplikace modelu Windows Forms a v něm máte obslužnou rutinu události pro tuto metodu spolu s logikou aktualizace. Chcete-li ladit tento, jednoduše připojte před tlačítko stiskne, pak nastavte zarážku (ujistěte se, že otevřete odpovídající archivovaný soubor a nastavte zarážku existuje).  
  
   Použití <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> vlastnost, která se má vyvolat <xref:System.Deployment.Application> rozhraní API, jenom když je aplikace nasazená, rozhraní API musí být volána během ladění v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Viz také:  
 <xref:System.Deployment.Application>