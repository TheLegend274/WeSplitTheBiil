//
//  ContentView.swift
//  Project1
//
//  Created by Mathew Sabu on 7/29/23.
//

//Checking building app
import SwiftUI

struct ContentView: View
{
    @State private var checkAmount = 0.0 // the total starts at 0
    
    var totalPerPerson:Double{
        let peopleCount = Double(numberOfPeople + 2) // starts from 2 rather than 0.
        let tipSelection = Double(tipPercentage)
        let tipValue = checkAmount / 100 * tipSelection
        let grandTotal = checkAmount + tipValue
        let amountPerPerson = grandTotal/peopleCount
        
        return amountPerPerson
    }
    @State private var numberOfPeople = 2
    @State private var tipPercentage = 20
    @FocusState private var AmountIsFocused:Bool // for the UI
    let  tipPercentages = [10,20,25,0]
    
    
    
    var body: some View
    
{
        NavigationView
        {
            Form
            {
                Section
                {
                    //currency of the money
                    TextField("Amount", value: $checkAmount, format:.currency(code: Locale.current.currencyCode ?? "USD"))
                    .keyboardType(.decimalPad)
                    .focused($AmountIsFocused)
                    
                    
                    //this is a scroll thing
                    Picker("Number of People", selection: $numberOfPeople){
                        // from 2-99
                        ForEach(2..<100)
                        {
                            // shows the text in gray
                            Text("\($0) people")
                        }
                    }
                }
                
                Section {
                   Picker("Tip Percentage", selection: $tipPercentage) {
                        ForEach(tipPercentages, id: \.self) { // loops through each percentage.
                            Text($0, format:.percent) // prints the percentage as a percent
                        }
                    }
                    .pickerStyle(.segmented) //makes it into a row
                }header:{
                    Text("How much tip do you want to leave?") // header of the percentage
                }
                
                
                Section
                {
                    // this is the 3 bar where it shows the amount of the money updated
                    Text(totalPerPerson, format:
                            .currency(code: Locale.current.currencyCode ?? "USD"))
                }header:{
                    Text("Total per Person")
                }
            }
            .navigationTitle("WeSplit") //attached to the form
            .toolbar{
                ToolbarItemGroup(placement: .keyboard){
                    Spacer() // puts the done to the right hand side
                    Button("Done"){
                        AmountIsFocused = false // takes the UI back down
                    }
                }
            }
        }
        
        
    }
    
    
    struct ContentView_Previews: PreviewProvider
    {
        static var previews: some View
        {
            ContentView()
        }
    }
    
}
