---
title: 'Postupy: Správa více vláken ve spravovaném kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e597f46160221b19fe678bbf665782d3f3f5a249
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636422"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Postupy: Správa více vláken ve spravovaném kódu
Pokud máte spravované rozšíření VSPackage, která volá asynchronní metody nebo má operace, které jsou spouštěny na vlákna kromě vlákna uživatelského rozhraní Visual Studio, postupujte podle pokynů uvedených níže. Vlákna uživatelského rozhraní můžete zachovat responzivní, protože není nutné čekat pro práci v jiném vlákně, k dokončení. Můžete provést kódu efektivnější, protože není nutné další vlákna, které zabírají prostor v zásobníku a je možné provádět spolehlivější a snadněji ladit, protože zabránit zablokování a konflikty. program přestane reagovat.  
  
 Obecně platí, můžete přepnout z vlákna uživatelského rozhraní do jiného vlákna, nebo naopak. Po návratu metody, aktuální vlákno je vlákno, ze kterého byla původně volána.  
  
> [!IMPORTANT]
>  Tyto pokyny používají rozhraní API v <xref:Microsoft.VisualStudio.Threading> obor názvů, zejména <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> třídy. Rozhraní API v tomto oboru názvů jsou novinkou [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Můžete získat instanci <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> vlastnost `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Přepnout z vlákna uživatelského rozhraní na vlákně na pozadí  
  
1.  Pokud jsou ve vlákně uživatelského rozhraní a chcete provést asynchronní práce na vlákně na pozadí, použijte `Task.Run()`:  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Pokud jste ve vlákně uživatelského rozhraní a chcete synchronně blokovat, když se provede práci na vlákně na pozadí, použijte <xref:System.Threading.Tasks.TaskScheduler> vlastnost `TaskScheduler.Default` uvnitř <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Přepnout na vlákno uživatelského rozhraní z vlákna na pozadí  
  
1.  Pokud jste na vlákně na pozadí a chcete udělat něco na vlákně uživatelského rozhraní, použijte <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Můžete použít <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metoda přepnout na vlákno uživatelského rozhraní. Tato metoda odešle zprávu do vlákna uživatelského rozhraní s pokračováním aktuální asynchronní metody a taky komunikuje se službou rest rozhraní dělení na vlákna nastaví správnou prioritu a zabránit zablokování.  
  
     Pokud není asynchronní metodu vlákno na pozadí a nemůže provádět asynchronní, můžete stále použít `await` syntaxe přepnout na vlákno uživatelského rozhraní obalením svoji práci s <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, jako v tomto příkladu:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```