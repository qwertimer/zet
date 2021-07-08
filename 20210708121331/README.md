# Learning Go [Part 4]

# ----------------------------- Interfaces in Go -----------------------------

An interface is a type that attaches to another type and describes what the type can do. A simple example is building a printer scanner fax interface.

type Printer interface{
  Print() string

type Scanner interface {
  Scan() string
}

type Faxer interface {
  Fax() string
}


- Interface joiners
type PrinterScanner interface {

  Printer
  Scanner
}

type FaxerPrinterScanner interface {
  Faxer
  Printer
  Scanner
}


- Functions using the interfaces 

type myPrinter struct {}

func(mp myPrinter) Print() string{
  return "printing one page"

func (mp myPrinter) Scan() string {
  return "Scanned One Page"
  }


func (my myPrinter) Fax() string {
  return "Faxed One Pages"
}


type secondPrinter struct{}

func (sp secondPrinter) Print() string {
  return "Printing five pages"
}

func (sp secondPrinter) Scan() String {
  return "Scanned five pages"
}

func (sp secondPrinter) Fax() string {
  return "Faxed Five Pages"
}



func process(equipment FaxerPrinterScanner){
  fmt.Println("Running Print, equipment.Print())

  fmt.Println("Running Scan, equipment.Scan())
  fmt.Println("Running Fax, equipment.Fax())
}

func main() {
  printer := myPrinter{}
  otherPrinter := secondPrinter{}
  process(printer)
