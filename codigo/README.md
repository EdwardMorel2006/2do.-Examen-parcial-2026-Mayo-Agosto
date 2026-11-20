using System;
using System.Windows.Forms;

namespace Examen_Cafeteria_EdwardAlberMorelRamirez
{
    public partial class Form1 : Form
    {
       
        private decimal subtotal = 0m;

        public Form1()
        {
            InitializeComponent();

            // Conecta cada botón con su método.
            btnAgregar.Click += btnAgregar_Click;
            btnCalcular.Click += btnCalcular_Click;
            btnLimpiar.Click += btnLimpiar_Click;
            btnSalir.Click += btnSalir_Click;

          
            ReiniciarPedido();
        }

        // Limpia el pedido y restablece los valores iniciales.
        private void ReiniciarPedido()
        {
            subtotal = 0m;

            txtCliente.Clear();
            dtpFecha.Value = DateTime.Today;
            chkFrecuente.Checked = false;

            txtProducto.Clear();
            txtPrecio.Clear();
            nudCantidad.Value = 1;
            rbtNormal.Checked = true;
            chkPorcionExtra.Checked = false;
            rbtLocal.Checked = true;

            lstPedido.Items.Clear();

            lblSubtotal.Text = "RD$ 0.00";
            lblDescuento.Text = "RD$ 0.00";
            lblEmpaque.Text = "RD$ 0.00";
            lblItbis.Text = "RD$ 0.00";
            lblTotal.Text = "RD$ 0.00";
        }

        
        private void btnAgregar_Click(object sender, EventArgs e)
        {
            // Valida que el nombre del producto no esté vacío.
            if (txtProducto.Text.Trim() == "")
            {
                MessageBox.Show("Escriba el nombre del producto.");
                txtProducto.Focus();
                return;
            }

            // Valida que el precio sea numérico y mayor que cero.
            if (!decimal.TryParse(txtPrecio.Text, out decimal precioBase) || precioBase <= 0)
            {
                MessageBox.Show("Escriba un precio válido.");
                txtPrecio.Focus();
                return;
            }

            // El precio unico inicia con el precio escrito.
            decimal precioUnitario = precioBase;

  
            if (rbtGrande.Checked)
                precioUnitario += 25m;

           
            if (chkPorcionExtra.Checked)
                precioUnitario += 30m;

           
            int cantidad = (int)nudCantidad.Value;
            decimal totalLinea = precioUnitario * cantidad;

          
            subtotal += totalLinea;

            // Crea el nombre que se mostrará en la lista.
            string detalle = txtProducto.Text.Trim();

            if (rbtGrande.Checked)
                detalle += " (Grande)";
            else
                detalle += " (Normal)";

            if (chkPorcionExtra.Checked)
                detalle += " + Extra";

            // Crea una línea alineada para el ListBox.
            string linea = cantidad.ToString().PadRight(6) +
                           detalle.PadRight(24) +
                           precioUnitario.ToString("0.00").PadLeft(10) +
                           totalLinea.ToString("0.00").PadLeft(12);

            lstPedido.Items.Add(linea);

            // Limpia los controles para agregar otro producto.
            txtProducto.Clear();
            txtPrecio.Clear();
            nudCantidad.Value = 1;
            rbtNormal.Checked = true;
            chkPorcionExtra.Checked = false;
            txtProducto.Focus();
        }

        // Calcula descuento, empaque, ITBIS y total final.
        private void btnCalcular_Click(object sender, EventArgs e)
        {
            // No permite calcular si no hay productos.
            if (lstPedido.Items.Count == 0)
            {
                MessageBox.Show("Agregue al menos un producto.");
                return;
            }

         
            decimal descuento = chkFrecuente.Checked ? subtotal * 0.10m : 0m;

            decimal empaque = rbtLlevar.Checked ? 20m : 0m;

            // Calcula impuesto y total a pagar.
            decimal baseImponible = subtotal - descuento + empaque;
            decimal itbis = baseImponible * 0.18m;
            decimal total = baseImponible + itbis;

            // Muestra los resultados en el formulario.
            lblSubtotal.Text = $"RD$ {subtotal:0.00}";
            lblDescuento.Text = $"RD$ {descuento:0.00}";
            lblEmpaque.Text = $"RD$ {empaque:0.00}";
            lblItbis.Text = $"RD$ {itbis:0.00}";
            lblTotal.Text = $"RD$ {total:0.00}";
        }

       
        private void btnLimpiar_Click(object sender, EventArgs e)
        {
            ReiniciarPedido();
        }

        // Solicita confirmación antes de cerrar el programa.
        private void btnSalir_Click(object sender, EventArgs e)
        {
            DialogResult respuesta = MessageBox.Show(
                "¿Desea salir del programa?",
                "Salir",
                MessageBoxButtons.YesNo,
                MessageBoxIcon.Question);

            if (respuesta == DialogResult.Yes)
                Close();
        }

      
        private void txtCliente_TextChanged(object sender, EventArgs e)
        {
        }

        private void dtpFecha_ValueChanged(object sender, EventArgs e)
        {
        }

        private void txtProducto_TextChanged(object sender, EventArgs e)
        {
        }

        private void groupBox1_Enter(object sender, EventArgs e)
        {
        }

        private void chkPorcionExtra_CheckedChanged(object sender, EventArgs e)
        {
        }

        private void label1_Click_1(object sender, EventArgs e)
        {
        }

        private void label6_Click(object sender, EventArgs e)
        {
        }

        private void label10_Click(object sender, EventArgs e)
        {
        }

        private void Form1_Load(object sender, EventArgs e)
        {
        }
    }
}
