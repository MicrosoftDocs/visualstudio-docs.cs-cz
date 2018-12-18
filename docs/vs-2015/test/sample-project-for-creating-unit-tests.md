---
title: Ukázkový projekt testování částí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: c3d364ffe23e79bb8842770bec0602d4bb7022c9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248583"
---
# <a name="sample-project-for-creating-unit-tests"></a>Ukázkový projekt testů jednotek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento ukázkový kód je k dispozici pro použití v následujících návodech:  
  
-   [Návod: Vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Tento názorný postup vás provede kroky k vytvoření a přizpůsobení testů jednotek, je spustit a podívejte se na výsledky testu.  
  
-   [Návod: Spuštění testů a pokrytí kódu zobrazit](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). Tento návod ukazuje, jak zobrazit data o pokrytí kódu, který znázorňuje podíl kódu projektu, který je právě testováno.  
  
-   [Návod: použití testování z příkazového řádku](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). V tomto názorném postupu použijete ke spuštění testů a zobrazit výsledky nástroje příkazového řádku MSTest.exe.  
  
## <a name="sample-code"></a>Ukázkový kód  
 Pouze touto úmyslnou chybou v této ukázce je, že v metoda debetní "m_balance += částka" by měla mít minus není plus podepsat před znaménko rovná se.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 / * Vzorové společnosti, organizace, produkty, názvy domén, e-mailové adresy, loga, osoby, místa a události použité v ukázkách jsou smyšlené.  Žádné jejich spojení se skutečnou společností, organizaci, produktu, název domény, e-mailovou adresu, loga, osoby, místa nebo události je určena ji vyvozovat. \*/  
  
## <a name="working-with-the-code"></a>Práce s kódem  
 Pro práci s tímto kódem je nejprve nutné pro něj vytvořit projekt v sadě [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Postupujte podle kroků v části "Příprava návodu" [Walkthrough: Creating and Running testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Návod: Spuštění testů a zobrazení pokrytí kódu](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Návod: použití nástroje příkazového řádku test](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)



