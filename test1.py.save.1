#!/usr/bin/env python
import clutter
import gtk
import math
import sys
import os
import magic

class BrowserPane:

	def __init__(self, (pane_size_x, pane_size_y), background, current_directory):
		self.x = pane_size_x
		self.y = pane_size_y
		self.stage = clutter.Stage()
		self.stage.set_size(self.x, self.y)
		self.stage.set_color(clutter.color_parse(background))
		self.current_directory = current_directory
		self.folders = {}
		current_folder = self.get_folder(self.current_directory)
		current_folder.set_size(self.x, self.y)
		current_folder.show()
		print str(current_folder.get_position())
		self.stage.add(current_folder)

	def get_folder(self, folder):
		if folder not in self.folders.keys():
			self.folders[folder] = FolderView((self.x/2, self.y/2), "#FFFF00", folder, 8)
		return self.folders[folder]

	def main(self):
		self.stage.show_all()
		#self.stage.connect("key-press-event", self.input_keys)
		clutter.main()

class FolderView(clutter.Group):

	def __init__(self, (pane_size_x, pane_size_y), background, current_directory, row_size):
		super(FolderView, self).__init__()
		self.x = pane_size_x
		self.y = pane_size_y
		#self.default_size = (default_size_x, default_size_y)
		#self.row_size = int(math.floor(self.x / self.default_size[0]))
		self.row_size = row_size
		self.default_size = (self.x / self.row_size, self.x/self.row_size)
		self.rows = {0:{}}
		for x in range(0, self.row_size):
			self.rows[0][x] = 0
		self.view = clutter.Group()
		self.view.set_size(self.x, self.y)
		self.view.set_clip(0, 0, self.x, self.y)
		self.add(self.view)
		back = clutter.Rectangle()
		back.set_size(self.x, self.y)
		back.set_color(clutter.color_parse(background))
		self.view.add(back)
		self.current_directory = current_directory
		self.populate_display()

	def add_row(self):
		row_number = len(self.rows.keys())
		self.rows[row_number] = {}
		for x in range(0, self.row_size):
			self.rows[row_number][x] = 0

	def get_handler(self, type):
		def unhandled(filename):
			return None
		def handle_image_gdk(filename):
			try:
				pixbuf = gtk.gdk.pixbuf_new_from_file(filename)
			except Exception:
				print "Error: Couldn't load image " + filename
			else:
				return clutter.Texture(pixbuf)
		for format in gtk.gdk.pixbuf_get_formats():
			if format['name'] == type.lower():
				return handle_image_gdk
		return unhandled

	def add_item(self, texture):
		self.view.add(texture)
		self.texture = texture
		position = (-1, -1)
		for row in range(0, len(self.rows.keys())):
			for column in range(0, self.row_size):
				if self.rows[row][column] == 0 and position == (-1, -1):
					position = (column, row)
					self.rows[row][column] = 1
		if position == (-1, -1):
			self.add_row()
			for row in range(0, len(self.rows.keys())):
				for column in range(0, self.row_size):
					if self.rows[row][column] == 0 and position == (-1, -1):
						position = (column, row)
						self.rows[row][column] = 1
			if position == (-1, -1):
				print "Error: Couldn't find space for icon"
				return

		print str(((self.default_size[0] * position[0], self.default_size[1] * position[1])))
		if texture.get_size()[0] / self.default_size[0] > texture.get_size()[1] / self.default_size[1]:
			texture.set_scale((self.default_size[0] + 0.0) / (texture.get_size()[0] + 0.0), (self.default_size[0] + 0.0) / (texture.get_size()[0] + 0.0))
		else:
			texture.set_scale((self.default_size[1] + 0.0) / (texture.get_size()[1] + 0.0), (self.default_size[1] + 0.0) / (texture.get_size()[1] + 0.0))
		texture.set_position(self.default_size[0] * position[0], self.default_size[1] * position[1])
		texture.show()
		self.view.show_all()

	#def input_keys(self, stage, event):
	#	key = gtk.gdk.keyval_name(event.keyval)
	#	self.timelines[key].start()
	#	self.timelines["Opacity"].start()

	def populate_display(self):
		items = []
		files = os.listdir(self.current_directory)
		files.sort()
		for item in files:
			items.append(self.get_icon(item))
		while None in items:
			items.pop(items.index(None))
		for item in items:
			self.add_item(item)
			#except Exception:
			#	print "Error: Could not display icon"

	def get_icon(self, filename):
		type_finder = magic.open(magic.MAGIC_NONE)
		type_finder.load()
		type = type_finder.file(self.current_directory + filename).split()[0].lower()
		icon = self.get_handler(type)(self.current_directory + filename)
		if icon is not None:
			return icon

	#def main(self):
	#	self.stage.show()
	#	self.stage.connect("key-press-event", self.input_keys)
	#	clutter.main()

if __name__ == '__main__':
	current_directory = os.getcwd()

	current_directory = '/home/chris/Pictures/'

	browser = BrowserPane((800, 600), "#FFFFFF", current_directory)		# Makes an 800x600 black window

	browser.main()
